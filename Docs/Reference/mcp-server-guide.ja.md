# MCPサーバー トラブルシューティングガイド

**MCPサーバー概要**: Model Context Protocol（MCP）サーバーは、ドキュメント検索（Context7）、UI生成（Magic）、高度な推論（Sequential）などの拡張機能を提供します。本ガイドでは、すべてのMCPサーバーのインストール、設定、および運用上のトラブルシューティングについて説明します。

**サーバー固有のソリューション**: 各MCPサーバーには独自の要件と一般的な障害パターンがあります。本ガイドでは、各サーバータイプに対する対象を絞ったソリューションと、一般的なMCPトラブルシューティング戦略を提供します。

## MCPサーバー概要

### 利用可能なMCPサーバー

**コアMCPサーバー：**
- **Context7**: 公式ドキュメント検索とフレームワークパターン
- **Sequential**: マルチステップ推論と複雑な分析
- **Magic**: 21st.devパターンからのモダンUIコンポーネント生成
- **Playwright**: ブラウザー自動化とE2Eテスト
- **Morphllm**: トークン最適化によるパターンベースのコード編集
- **Serena**: セマンティックコード理解とプロジェクトメモリ

**サーバー要件：**
- Node.js 16.0.0以上
- npmまたはyarnパッケージマネージャー
- 一部のサーバーに対する安定したネットワーク接続
- 十分なシステムメモリ（2GB以上推奨）

## インストールと設定の問題

### Node.jsとnpmの問題

#### 問題: Node.jsバージョン非互換性
**エラーメッセージ**: `ERROR: MCP servers require Node.js 16+ but found Node.js 14.x`

**診断**:
```bash
node --version
npm --version
```

**解決策1**: Node.jsのアップデート（Linux/Ubuntu）
```bash
curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
```

**解決策2**: Node Version Manager（nvm）の使用
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
source ~/.bashrc
nvm install node
nvm use node
```

**解決策3**: 手動Node.jsインストール
- https://nodejs.org/ からダウンロード
- プラットフォーム固有のインストール手順に従う

**検証**:
```bash
node --version  # 16.0.0以上である必要があります
npm --version   # 8.0.0以上である必要があります
```

**問題: npm権限の問題**
```bash
# エラーメッセージ
ERROR: EACCES: permission denied, access '/usr/local/lib/node_modules'

# 解決策1: ユーザーディレクトリ用にnpmを設定
mkdir ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.profile
source ~/.profile

# 解決策2: npm権限の修正
sudo chown -R $(whoami) $(npm config get prefix)/{lib/node_modules,bin,share}

# 解決策3: パッケージ実行にnpxを使用
npx @context7/mcp-server --version

# 検証
npm list -g --depth=0
npm config get prefix
```

### MCPサーバーインストール失敗

**問題: Context7 MCPサーバーインストール失敗**
```bash
# エラーメッセージ
ERROR: Failed to install @context7/mcp-server

# 診断
npm list -g @context7/mcp-server
node --version

# 解決策1: npmキャッシュをクリアして再インストール
npm cache clean --force
npm install -g @context7/mcp-server

# 解決策2: 代替レジストリを使用
npm install -g @context7/mcp-server --registry https://registry.npmjs.org/

# 解決策3: 手動インストール検証
npm info @context7/mcp-server
npm install -g @context7/mcp-server@latest

# 検証
npm list -g @context7/mcp-server
node -e "console.log('Context7 installation test')"
```

**問題: Sequential MCPサーバーの依存関係が不足**
```bash
# エラーメッセージ
ERROR: Sequential MCP server missing required dependencies

# 診断
npm list -g @sequential/mcp-server
npm list -g | grep -E "typescript|@types"

# 解決策1: 依存関係を明示的にインストール
npm install -g typescript @types/node
npm install -g @sequential/mcp-server

# 解決策2: 依存関係付きで強制再インストール
npm uninstall -g @sequential/mcp-server
npm install -g @sequential/mcp-server --save-dev

# 解決策3: パッケージの整合性をチェック
npm audit --global
npm update -g

# 検証
npm list -g @sequential/mcp-server
```

**問題: Magic UIジェネレーターのインストール問題**
```bash
# エラーメッセージ
ERROR: @magic/ui-generator installation failed - build dependencies missing

# 診断
npm list -g @magic/ui-generator
which gcc make  # ビルドツールをチェック

# 解決策1: ビルド依存関係のインストール（Linux）
sudo apt install build-essential python3-dev

# 解決策2: ビルド依存関係のインストール（macOS）
xcode-select --install

# 解決策3: プリビルドバイナリの使用
npm install -g @magic/ui-generator --ignore-scripts

# 検証
npm list -g @magic/ui-generator
```

## 接続と通信の問題

### MCPサーバー接続失敗

**問題: Context7サーバーが接続しない**
```bash
# エラーメッセージ
ERROR: MCP server 'context7' failed to connect

# 診断
# Node.jsインストールをチェック
node --version  # 16.0.0以上である必要があります
npm list -g @context7/mcp-server

# サーバー設定をチェック
cat ~/.claude/CLAUDE.md | grep -i context7

# 解決策1: Claude Codeセッションを再起動
# MCPサーバーはClaude Codeセッション再起動で再起動されます

# 解決策2: MCPサーバーを再設定
python3 -m SuperClaude install --components mcp --force

# 解決策3: 手動サーバーテスト
node -e "console.log('Node.js working')"
npm test @context7/mcp-server

# 解決策4: ネットワーク接続をチェック
ping context7-server.example.com  # サーバーがネットワークを必要とする場合
curl -I https://context7-api.example.com/health  # ヘルスチェック

# 検証
# Claude CodeでContext7機能を試す
# ドキュメント要求に応答するはずです
```

**問題: MCPサーバー通信タイムアウト**
```bash
# エラーメッセージ
ERROR: MCP server request timeout after 30 seconds

# 診断
# ネットワーク接続とサーバーヘルスをチェック
ping 8.8.8.8  # 基本的な接続性
curl -I https://api.example.com/health  # APIヘルス

# システムリソースをチェック
top
free -h

# 解決策1: 操作の複雑さを減らす
# 複雑なタスクをより小さな部分に分割

# 解決策2: Claude Codeセッションを再起動
# MCPサーバーはClaude Codeセッション再起動で再起動されます

# 解決策3: 問題のあるサーバーを一時的に無効化
# 操作に--no-mcpフラグを使用

# 解決策4: タイムアウトを増やす（設定可能な場合）
# MCPサーバー設定ファイルをチェック

# 検証
# 最初は簡単な操作でテスト
# 徐々に複雑さを増やす
```

**問題: 複数のMCPサーバーが競合**
```bash
# エラーメッセージ
ERROR: MCP server port conflicts detected

# 診断
netstat -tlnp | grep :8000  # ポート使用状況をチェック
ps aux | grep -E "context7|sequential|magic"

# 解決策1: 順次サーバー再起動
# Claude Codeを再起動してすべてのMCPサーバーをリセット

# 解決策2: 異なるポートを設定
# MCPサーバー設定ファイルを編集
# 通常は~/.claude/またはサーバー固有のディレクトリにあります

# 解決策3: 選択的サーバーアクティベーションを使用
# --all-mcpの代わりに特定のサーバーフラグを使用

# 検証
netstat -tlnp | grep -E "8000|8001|8002"  # ポート割り当てをチェック
```

## サーバー固有のトラブルシューティング

### Context7ドキュメントサーバー

**問題: Context7がドキュメントを見つけない**
```bash
# 症状: Context7がアクティブだがドキュメントを返さない

# 診断
# Context7接続をテスト
node -e "const c7 = require('@context7/mcp-server'); console.log('Context7 loaded');"

# 解決策1: Context7サーバーをアップデート
npm update -g @context7/mcp-server

# 解決策2: Context7キャッシュをクリア
rm -rf ~/.context7/cache/  # キャッシュディレクトリが存在する場合

# 解決策3: 明示的なライブラリキーワードを使用
# リクエストで特定のフレームワーク名を使用

# 解決策4: インターネット接続を確認
curl -I https://docs.react.dev/  # API テストの例

# 検証
# 特定のドキュメントリクエストを試す
# 関連するフレームワーク情報を返すはずです
```

**問題: Context7が古い情報を返す**
```bash
# 症状: Context7が古いドキュメントバージョンを返す

# 解決策1: Context7サーバーをアップデート
npm uninstall -g @context7/mcp-server
npm install -g @context7/mcp-server@latest

# 解決策2: ドキュメントキャッシュをクリア
rm -rf ~/.context7/  # キャッシュが存在する場合はクリア

# 解決策3: ドキュメントリフレッシュを強制
# Claude Codeセッションを完全に再起動

# 検証
# レスポンスのドキュメント日付をチェック
# 現在のフレームワークバージョンを返すはずです
```

### Sequential推論サーバー

**問題: Sequentialサーバー内部エラー**
```bash
# エラーメッセージ
ERROR: Sequential reasoning server encountered internal error

# 診断
# Sequentialサーバーログをチェック
tail -f ~/.claude/logs/sequential-mcp.log  # ログが存在する場合

# サーバーインストールをチェック
npm list -g @sequential/mcp-server

# 解決策1: Claude Codeセッションを再起動
# これによりSequentialを含むすべてのMCPサーバーが再起動されます

# 解決策2: 代替の推論アプローチを使用
# MCPサーバーなしでネイティブClaude推論を使用

# 解決策3: Sequential MCPを再インストール
npm uninstall -g @sequential/mcp-server
npm install -g @sequential/mcp-server@latest

# 解決策4: メモリ可用性をチェック
free -h  # 複雑な推論に十分なメモリを確保

# 検証
# 最初は簡単な分析タスクでテスト
# 構造化された推論出力を提供するはずです
```

**問題: Sequentialサーバーメモリオーバーロード**
```bash
# 症状: Sequentialサーバーがクラッシュするか応答しなくなる

# 診断
top | grep -E "sequential|node"
free -h

# 解決策1: 分析の複雑さを減らす
# 複雑な問題をより小さな部分に分割

# 解決策2: システムメモリまたはスワップを増やす
sudo swapon --show  # スワップ状況をチェック

# 解決策3: スコープ制限を使用
# 特定のコンポーネントに分析を集中

# 検証
ps aux | grep sequential  # プロセス状況をチェック
```

### Magic UIジェネレーター

**問題: MagicがUIコンポーネントを生成しない**
```bash
# 症状: UIコンポーネントリクエストが期待される出力を生成しない

# 診断
# Magicサーバーインストールをチェック
npm list -g @magic/ui-generator
cat ~/.claude/CLAUDE.md | grep -i magic

# 解決策1: Magicサーバーインストールを確認
npm list -g @magic/ui-generator
npm install -g @magic/ui-generator@latest

# 解決策2: 明示的なMagicアクティベーションを使用
# "component"、"UI"、または"interface"キーワードを含める

# 解決策3: コンポーネントリクエスト形式をチェック
# より良いMagicアクティベーションのために記述的なリクエストを使用

# 解決策4: Magicサーバーを直接テスト
node -e "const magic = require('@magic/ui-generator'); console.log('Magic loaded');"

# 検証
# モダンパターンで完全なUIコンポーネントを生成するはずです
```

**問題: Magicコンポーネントがフレームワーク準拠でない**
```bash
# 症状: 生成されたコンポーネントがフレームワークパターンと一致しない

# 解決策1: フレームワーク固有のキーワードを使用
# リクエストに"React"、"Vue"、"Angular"を含める

# 解決策2: Context7と組み合わせる
# フレームワーク準拠コンポーネントのためにMagicとContext7の両方を使用

# 解決策3: Magicサーバーをアップデート
npm update -g @magic/ui-generator

# 検証
# 生成されたコンポーネントはフレームワーク規約に従うはずです
```

### Playwrightブラウザー自動化

**問題: Playwrightブラウザーインストール失敗**
```bash
# エラーメッセージ
ERROR: Playwright browser automation failed - browser not installed

# 診断
npm list -g playwright
npx playwright --version

# 解決策1: Playwrightブラウザーをインストール
npx playwright install
npx playwright install-deps

# 解決策2: 特定のブラウザーをインストール
npx playwright install chromium
npx playwright install firefox
npx playwright install webkit

# 解決策3: ブラウザー依存関係を修正（Linux）
sudo apt-get install libnss3 libatk-bridge2.0-0 libdrm2 libgtk-3-0

# 検証
npx playwright --version
ls ~/.cache/ms-playwright/  # ブラウザーインストールをチェック
```

**問題: Playwrightブラウザー起動失敗**
```bash
# エラーメッセージ
ERROR: Browser launch failed - display not available

# 診断
echo $DISPLAY  # X11ディスプレイをチェック
ps aux | grep Xvfb  # 仮想ディスプレイをチェック

# 解決策1: ヘッドレスモードを使用
# Playwright設定でheadless: trueを設定

# 解決策2: 仮想ディスプレイをインストール（Linux）
sudo apt-get install xvfb
export DISPLAY=:99
Xvfb :99 -screen 0 1024x768x24 &

# 解決策3: ブラウザーテストにDockerを使用
docker run -it --rm playwright:latest

# 検証
# ヘッドレスモードでブラウザーを正常に起動するはずです
```

### Morphllmパターンエディター

**問題: Morphllmパターン適用失敗**
```bash
# 症状: パターンベースの編集が正しく適用されない

# 診断
npm list -g @morphllm/mcp-server

# 解決策1: Morphllmサーバーをアップデート
npm update -g @morphllm/mcp-server

# 解決策2: より具体的なパターンを使用
# 明示的なパターン記述を提供

# 解決策3: ファイル権限をチェック
ls -la target-files/  # 書き込み権限を確保

# 検証
# パターン編集はファイル全体に一貫して適用されるはずです
```

### Serenaプロジェクトメモリ

**問題: Serenaセッション永続化失敗**
```bash
# 症状: プロジェクトコンテキストがセッション間で永続化されない

# 診断
ls ~/.claude/sessions/  # セッションストレージをチェック
ls ~/.serena/  # Serena固有のストレージをチェック

# 解決策1: セッション保存操作を確認
# 終了前に適切なセッション保存を確保

# 解決策2: ストレージ権限をチェック
ls -la ~/.claude/sessions/
chmod 755 ~/.claude/sessions/

# 解決策3: Serenaサーバーを再インストール
npm uninstall -g @serena/mcp-server
npm install -g @serena/mcp-server@latest

# 検証
# セッションコンテキストはClaude Code再起動後も持続するはずです
```

## パフォーマンスと最適化

### MCPサーバーパフォーマンス問題

**問題: 遅いMCPサーバーレスポンス時間**
```bash
# 症状: MCPサーバー操作が遅延を引き起こす

# 診断
# MCPサーバーのインストールとヘルスをチェック
npm list -g | grep -E "context7|sequential|magic|playwright"
top | grep node

# 解決策1: 選択的MCPサーバー使用
# 特定のタスクに必要なサーバーのみを使用

# 解決策2: Claude Codeセッションを再起動
# これによりすべてのMCPサーバーが新しく再起動されます

# 解決策3: ローカルフォールバックモード
# 純粋にネイティブ操作に--no-mcpフラグを使用

# 解決策4: すべてのMCPサーバーをアップデート
npm update -g

# 検証
time node -e "console.log('Node.js speed test')"
# 正常に完了するはずです
```

**問題: MCPサーバーメモリリーク**
```bash
# 症状: 時間の経過とともにメモリ使用量が増加

# 診断
top | grep node  # Node.jsプロセスを監視
ps aux --sort=-%mem | head -10

# 解決策1: 定期的なClaude Codeセッション再起動
# 大量使用中は定期的にセッションを再起動

# 解決策2: 特定のサーバーを監視
htop  # 個別のMCPサーバープロセスを監視

# 解決策3: メモリ効率的なパターンを使用
# MCPサーバーメモリに大きなデータセットを保持しない

# 検証
free -h  # メモリ使用量の傾向を監視
```

### リソース管理

**問題: 複数のMCPサーバーがリソースを競合**
```bash
# 症状: 複数のサーバーがアクティブな時にシステムが遅くなる

# 診断
top | grep -E "node|mcp"
iostat 1 3  # I/O使用量をチェック

# 解決策1: ターゲットサーバーアクティベーションを使用
# タスクごとに必要なサーバーのみをアクティブ化

# 解決策2: システムリソースを増やす
# 可能であればRAMやCPUコアを追加

# 解決策3: MCP操作をキューに入れる
# 同時の重い操作を避ける

# 解決策4: MCPサーバー優先度を使用
# MCP設定でリソース割り当てを設定

# 検証
top  # 操作中のリソース使用量を監視
```

## 高度なMCP設定

### カスタムMCPサーバー設定

**問題: デフォルトのMCP設定が最適でない**
```bash
# 症状: MCPサーバーが特定の使用例に対して最適に動作しない

# 解決策1: 設定ファイルを見つける
find ~/.claude/ -name "*mcp*" -type f
find ~/.config/ -name "*mcp*" -type f

# 解決策2: サーバー設定をカスタマイズ
# サーバー固有の設定ファイルを編集
# 一般的な場所: ~/.claude/mcp-config.json

# 解決策3: 環境変数設定
export MCP_CONTEXT7_TIMEOUT=60
export MCP_SEQUENTIAL_MEMORY_LIMIT=2048

# 検証
# カスタム設定でテスト
# 特定の使用例で改善されたパフォーマンスを表示するはずです
```

**問題: MCPサーバーロードバランシング**
```bash
# 症状: MCPサーバー間での不均等な負荷分散

# 解決策1: サーバー優先度を設定
# MCPサーバー設定を編集して負荷をバランス

# 解決策2: ラウンドロビンサーバー選択を使用
# サーバーコールでローテーションロジックを実装

# 解決策3: サーバーパフォーマンスを監視
# レスポンス時間を追跡し、それに応じて調整

# 検証
# サーバー間でバランスの取れたリソース使用量を観察
```

## デバッグと診断

### MCPサーバーヘルス監視

**包括的なMCPヘルスチェック：**
```bash
# MCPサーバーシステム診断
echo "=== MCPサーバーヘルスチェック ==="

# Node.js環境
echo "Node.jsバージョン: $(node --version)"
echo "npmバージョン: $(npm --version)"

# サーバーインストール
echo "=== インストール済みMCPサーバー ==="
npm list -g | grep -E "context7|sequential|magic|playwright|morphllm|serena"

# プロセス監視
echo "=== 実行中のMCPプロセス ==="
ps aux | grep -E "node.*mcp|mcp.*server" | head -5

# リソース使用量
echo "=== リソース使用量 ==="
echo "メモリ: $(free -h | grep Mem | awk '{print $3 "/" $2}')"
echo "CPU負荷: $(uptime | awk -F'load average:' '{print $2}')"

# ネットワーク接続（必要な場合）
echo "=== ネットワーク状況 ==="
ping -c 1 8.8.8.8 > /dev/null && echo "✅ ネットワーク OK" || echo "❌ ネットワーク問題"
```

**MCPサーバー機能テスト：**
```bash
# 各MCPサーバーを個別にテスト
echo "=== MCPサーバー機能テスト ==="

# Context7テスト
if npm list -g @context7/mcp-server > /dev/null 2>&1; then
    echo "✅ Context7インストール済み"
else
    echo "❌ Context7なし"
fi

# Sequentialテスト
if npm list -g @sequential/mcp-server > /dev/null 2>&1; then
    echo "✅ Sequentialインストール済み"
else
    echo "❌ Sequentialなし"
fi

# Magicテスト
if npm list -g @magic/ui-generator > /dev/null 2>&1; then
    echo "✅ Magicインストール済み"
else
    echo "❌ Magicなし"
fi

# Playwrightテスト
if npx playwright --version > /dev/null 2>&1; then
    echo "✅ Playwrightインストール済み"
else
    echo "❌ Playwrightなし"
fi
```

### MCPサーバーログ解析

**ログ収集と解析：**
```bash
# MCPサーバーログを収集
echo "=== MCPサーバーログ ==="

# 一般的なログ場所をチェック
find ~/.claude/ -name "*.log" -type f 2>/dev/null
find /tmp/ -name "*mcp*.log" -type f 2>/dev/null
find /var/log/ -name "*mcp*.log" -type f 2>/dev/null

# npmログをチェック
npm config get logs-max
ls ~/.npm/_logs/ 2>/dev/null | tail -5

# Node.jsプロセスのシステムログ
journalctl -u node* --since "1 hour ago" 2>/dev/null | tail -10
```

## 緊急復旧

### 完全なMCPリセット

**完全なMCPサーバーリセット手順：**
```bash
# 緊急MCPリセット
echo "=== 緊急MCPサーバーリセット ==="

# ステップ1: すべてのClaude Codeセッションを停止
echo "すべてのClaude Codeセッションを停止し、30秒待つ"

# ステップ2: 現在の状態をバックアップ
cp -r ~/.claude ~/.claude.mcp.backup.$(date +%Y%m%d)

# ステップ3: すべてのMCPサーバーを削除
npm list -g | grep -E "context7|sequential|magic|playwright|morphllm|serena" | awk '{print $2}' | xargs npm uninstall -g

# ステップ4: npmキャッシュをクリア
npm cache clean --force

# ステップ5: MCPサーバーを再インストール
python3 -m SuperClaude install --components mcp --force

# ステップ6: 検証
npm list -g | grep -E "context7|sequential|magic|playwright|morphllm|serena"

# ステップ7: 機能テスト
echo "再起動後にClaude CodeでMCPサーバーをテスト"
```

## 関連リソース

### MCP固有ドキュメント
- **コアSuperClaudeガイド**: [../User-Guide/mcp-servers.md](../User-Guide/mcp-servers.md) - MCPサーバー概要と使用法
- **一般的な問題**: [common-issues.md](./common-issues.md) - 一般的なトラブルシューティング手順
- **診断リファレンス**: [diagnostic-reference.md](./diagnostic-reference.md) - 高度な診断手順

### 外部リソース
- **Node.js公式**: [https://nodejs.org/](https://nodejs.org/) - Node.jsインストールとドキュメント
- **npmドキュメント**: [https://docs.npmjs.com/](https://docs.npmjs.com/) - パッケージマネージャードキュメント
- **Playwrightガイド**: [https://playwright.dev/](https://playwright.dev/) - ブラウザー自動化ドキュメント

### サポートチャンネル
- **GitHubイシュー**: [MCP固有の問題](https://github.com/SuperClaude-Org/SuperClaude_Framework/issues)
- **GitHubディスカッション**: [MCPサーバーコミュニティサポート](https://github.com/SuperClaude-Org/SuperClaude_Framework/discussions)

---

**MCPサーバー優先度**: トラブルシューティング時は、依存関係の順番でサーバーに対処する: Node.js → npm → 個別サーバー → Claude Code統合。ほとんどのMCP問題は適切なNode.jsセットアップとサーバー再インストールで解決します。

**検証パターン**: MCPソリューションの後、常に以下で検証する:
- ✅ `node --version` - 16.0.0以上である必要があります
- ✅ `npm list -g | grep mcp` - インストールされたサーバーを表示するはずです
- ✅ Claude Codeでサーバー機能をテスト - エラーなしで応答するはずです