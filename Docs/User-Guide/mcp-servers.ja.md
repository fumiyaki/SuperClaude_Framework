# SuperClaude MCPサーバーガイド

## 概要

MCP（Model Context Protocol）サーバーは、専門ツールを通じてClaude Codeの機能を拡張します。SuperClaudeは6つのMCPサーバーを統合し、タスクに基づいてそれらをアクティブ化するタイミングに関する指示をClaudeに提供します。

### 実態チェック

- **MCPサーバーとは何か**：追加ツールを提供する外部Node.jsプロセス
- **何ではないか**：内蔵のSuperClaude機能ではありません
- **アクティベーションの仕組み**：Claudeがコンテキストに基づいて適切なサーバーを使用するための指示を読みます
- **何を提供するか**：Claude Codeのネイティブ機能を拡張する実際のツール

**コアサーバー：**
- **context7**：公式ライブラリドキュメントとパターン
- **sequential-thinking**：マルチステップ推論と解析
- **magic**：モダンUIコンポーネント生成
- **playwright**：ブラウザー自動化とE2Eテスト
- **morphllm-fast-apply**：パターンベースのコード変換
- **serena**：セマンティックコード理解とプロジェクトメモリ

## クイックスタート

**セットアップ確認**：MCPサーバーは自動的にアクティブ化されます。インストールとトラブルシューティングについては、[インストールガイド](../Getting-Started/installation.md)と[トラブルシューティング](../Reference/troubleshooting.md)を参照してください。

**自動アクティベーションロジック：**

| リクエストに含まれる内容 | アクティブ化されるサーバー |
|-----------------|------------------|
| ライブラリインポート、API名 | **context7** |
| `--think`、デバッグ | **sequential-thinking** |
| `component`、`UI`、フロントエンド | **magic** |
| `test`、`e2e`、`browser` | **playwright** |
| マルチファイル編集、リファクタリング | **morphllm-fast-apply** |
| 大規模プロジェクト、セッション | **serena** |

## サーバー詳細

### context7

**目的**：公式ライブラリドキュメントアクセス
**トリガー**：インポート文、フレームワークキーワード、ドキュメントリクエスト
**要件**：Node.js 16+、APIキー不要

```bash
# 自動アクティベーション
/sc:implement "React認証システム"
# → 公式Reactパターンを提供

# 手動アクティベーション
/sc:analyze auth-system/ --c7
```

### sequential-thinking

**目的**：構造化マルチステップ推論と系統的解析
**トリガー**：複雑なデバッグ、`--think`フラグ、アーキテクチャ解析
**要件**：Node.js 16+、APIキー不要

```bash
# 自動アクティベーション
/sc:troubleshoot "APIパフォーマンス問題"
# → 系統的ルートコース解析を有効化

# 手動アクティベーション
/sc:analyze --think-hard architecture/
```

### magic

**目的**：21st.devパターンからのモダンUIコンポーネント生成
**トリガー**：UIリクエスト、`/ui`コマンド、コンポーネント開発
**要件**：Node.js 16+、TWENTYFIRST_API_KEY（必須）

```bash
# 自動アクティベーション
/sc:implement "レスポンシブダッシュボードコンポーネント"
# → モダンパターンでアクセシブルなUIを生成

# APIキー設定
export TWENTYFIRST_API_KEY="your_key_here"
```

### playwright

**目的**：リアルブラウザー自動化とE2Eテスト
**トリガー**：ブラウザーテスト、E2Eシナリオ、視覚的検証
**要件**：Node.js 16+、APIキー不要

```bash
# 自動アクティベーション
/sc:test --type e2e "ユーザーログインフロー"
# → ブラウザー自動化テストを有効化

# 手動アクティベーション
/sc:validate "アクセシビリティコンプライアンス" --play
```

### morphllm-fast-apply

**目的**：効率的なパターンベースのコード変換
**トリガー**：マルチファイル編集、リファクタリング、フレームワーク移行
**要件**：Node.js 16+、MORPH_API_KEY

```bash
# 自動アクティベーション
/sc:improve legacy-codebase/ --focus maintainability
# → ファイル間で一貫したパターンを適用

# APIキー設定
export MORPH_API_KEY="your_key_here"
```

### serena

**目的**：プロジェクトメモリ付きセマンティックコード理解
**トリガー**：シンボル操作、大規模コードベース、セッション管理
**要件**：Python 3.9+、uvパッケージマネージャー、APIキー不要

```bash
# 自動アクティベーション
/sc:load existing-project/
# → プロジェクト理解とメモリを構築

# 手動アクティベーション
/sc:refactor "UserServiceを抽出" --serena
```

## 設定

**MCP設定ファイル（`~/.claude.json`）：**

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "sequential-thinking": {
      "command": "npx", 
      "args": ["-y", "@modelcontextprotocol/server-sequential-thinking"]
    },
    "magic": {
      "command": "npx",
      "args": ["@21st-dev/magic"],
      "env": {"TWENTYFIRST_API_KEY": "${TWENTYFIRST_API_KEY}"}
    },
    "playwright": {
      "command": "npx",
      "args": ["@playwright/mcp@latest"]
    },
    "morphllm-fast-apply": {
      "command": "npx",
      "args": ["@morph-llm/morph-fast-apply"],
      "env": {"MORPH_API_KEY": "${MORPH_API_KEY}"}
    },
    "serena": {
      "command": "uv",
      "args": ["run", "serena", "start-mcp-server", "--context", "ide-assistant"],
      "cwd": "$HOME/.claude/serena"
    }
  }
}
```

## 使用パターン

**サーバー制御：**

```bash
# 特定のサーバーを有効化
/sc:analyze codebase/ --c7 --seq

# すべてのMCPサーバーを無効化
/sc:implement "シンプル関数" --no-mcp

# すべてのサーバーを有効化
/sc:design "複雑なアーキテクチャ" --all-mcp
```

**マルチサーバー調整：**

```bash
# フルスタック開発
/sc:implement "Eコマースチェックアウト"
# → Sequential：ワークフロー解析
# → Context7：決済パターン
# → Magic：UIコンポーネント
# → Serena：コード組織
# → Playwright：E2Eテスト
```

## トラブルシューティング

**よくある問題：**
- **サーバーが接続されない**：Node.jsをチェック：`node --version`（v16+が必要）
- **Context7が失敗**：キャッシュをクリア：`npm cache clean --force`
- **Magic/Morphllmエラー**：APIキーなしでは予想される（有料サービス）
- **サーバータイムアウト**：Claude Codeセッションを再起動

**クイックフィックス：**

```bash
# 接続をリセット
# Claude Codeセッションを再起動

# 依存関係をチェック
node --version  # v16+を表示するはず

# MCPなしでテスト
/sc:command --no-mcp

# 設定をチェック
ls ~/.claude.json
```

**APIキー設定：**

```bash
# Magicサーバー用（UI生成に必要）
export TWENTYFIRST_API_KEY="your_key_here"

# Morphllmサーバー用（バルク変換に必要）
export MORPH_API_KEY="your_key_here"

# 永続化のためにシェルプロファイルに追加
echo 'export TWENTYFIRST_API_KEY="your_key"' >> ~/.bashrc
echo 'export MORPH_API_KEY="your_key"' >> ~/.bashrc
```

**環境変数の使用：**
- ✅ `TWENTYFIRST_API_KEY` - Magic MCPサーバー機能に必要
- ✅ `MORPH_API_KEY` - Morphllm MCPサーバー機能に必要
- ❌ ドキュメント内の他の環境変数 - 例のみ、フレームワークでは使用されない
- 📝 両方とも有料サービスAPIキー、フレームワークはそれらなしでも動作

## サーバーの組み合わせ

**APIキーなし（無料）**：
- context7 + sequential-thinking + playwright + serena

**1つのAPIキー**：
- プロフェッショナルUI開発のためにmagicを追加

**2つのAPIキー**：
- 大規模リファクタリングのためにmorphllm-fast-applyを追加

**一般的なワークフロー：**
- **学習**：context7 + sequential-thinking
- **Web開発**：magic + context7 + playwright
- **エンタープライズリファクタリング**：serena + morphllm + sequential-thinking
- **複雑な解析**：sequential-thinking + context7 + serena

## 統合

**SuperClaudeコマンドとの統合：**
- 解析コマンドは自動的にSequential + Serenaを使用
- 実装コマンドはMagic + Context7を使用
- テストコマンドはPlaywright + Sequentialを使用

**行動モードとの統合：**
- ブレインストーミングモード：発見のためのSequential
- タスク管理：永続化のためのSerena
- オーケストレーションモード：最適なサーバー選択

**パフォーマンス制御：**
- システム負荷に基づく自動リソース管理
- 並行性制御：`--concurrency N`（1-15）
- 制約下での優先順位ベースサーバー選択

## 関連リソース

**必須リーディング：**
- [コマンドガイド](commands.md) - MCPサーバーをアクティブ化するコマンド
- [クイックスタートガイド](../Getting-Started/quick-start.md) - MCPセットアップガイド

**高度な使用：**
- [行動モード](modes.md) - モード-MCP調整
- [エージェントガイド](agents.md) - エージェント-MCP統合
- [セッション管理](session-management.md) - Serenaワークフロー

**技術リファレンス：**
- [例クックブック](../Reference/examples-cookbook.md) - MCPワークフローパターン
- [技術アーキテクチャ](../Developer-Guide/technical-architecture.md) - 統合詳細