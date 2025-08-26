# SuperClaude 一般的な問題 - クイックリファレンス 🚀

**問題解決ガイド**: 実用的な解決策を持つ最頻出問題。

## トップ5クイック修正（問題の90%）

### 1. Claude Codeでコマンドが動作しない ⚡
```
問題: /sc:brainstormが動作しない
解決策: Claude Codeを完全に再起動
テスト: /sc:brainstorm "test"で質問が返されるはず
```

### 2. インストール確認
```bash
python3 -m SuperClaude --version    # 4.0.8が表示されるはず

# 動作しない場合:
# pipxユーザーの場合
pipx upgrade SuperClaude

# pipユーザーの場合
pip install --upgrade SuperClaude

# 再インストール
python3 -m SuperClaude install
```

### 3. 権限問題
```bash
# 権限拒否 / PEP 668エラー:
# オプション1: pipxを使用（推奨）
pipx install SuperClaude

# オプション2: --userでpipを使用
pip install --user SuperClaude

# オプション3: 権限修正
sudo chown -R $USER ~/.claude
```

### 4. MCPサーバー問題
```bash
/sc:analyze . --no-mcp              # MCPサーバーなしでテスト
node --version                      # 必要に応じてNode.js 16+をチェック
```

### 5. コンポーネント不足
```bash
python3 -m SuperClaude install --components core commands agents modes --force
```

## プラットフォーム固有の問題

**Windows:**
```cmd
set CLAUDE_CONFIG_DIR=%USERPROFILE%\.claude
python -m SuperClaude install --install-dir "%CLAUDE_CONFIG_DIR%"
```

**macOS:**
```bash
brew install python3 node
pip3 install SuperClaude
```

**Linux:**
```bash
sudo apt install python3 python3-pip nodejs
pip3 install SuperClaude
```

## 確認チェックリスト
- [ ] `python3 -m SuperClaude --version`が4.0.8を返す
- [ ] Claude Codeで`/sc:brainstorm "test"`が動作する
- [ ] `SuperClaude install --list-components`がコンポーネントを表示

## クイック修正が効かない場合
高度な診断については[トラブルシューティングガイド](troubleshooting.md)を参照してください。