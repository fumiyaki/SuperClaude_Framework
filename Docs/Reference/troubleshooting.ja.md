# SuperClaude トラブルシューティングガイド 🔧

SuperClaude Frameworkの問題に対するクイック修正から高度診断まで。

## クイック修正（問題の90%）

**インストール確認:**
```bash
python3 -m SuperClaude --version    # 4.0.8が表示されるはず
SuperClaude install --list-components
```

**コマンド問題:**
```bash
# Claude Codeでテスト:
/sc:brainstorm "テストプロジェクト"        # 発見的質問が返されるはず

# 応答がない場合: Claude Codeセッションを再起動
```

**解決チェックリスト:**
- [ ] バージョンコマンドが動作し4.0.8を表示
- [ ] Claude Codeで`/sc:`コマンドが応答  
- [ ] MCPサーバーがリストされる: `SuperClaude install --list-components | grep mcp`

## 一般的な問題

### インストール問題

**パッケージインストール失敗:**
```bash
# pipxユーザーの場合
pipx uninstall SuperClaude
pipx install SuperClaude

# pipユーザーの場合
pip uninstall SuperClaude
pip install --upgrade pip
pip install SuperClaude
```

**権限拒否 / PEP 668エラー:**
```bash
# オプション1: pipxを使用（推奨）
pipx install SuperClaude

# オプション2: --userフラグでpipを使用
pip install --user SuperClaude

# オプション3: 権限を修正
sudo chown -R $USER ~/.claude

# オプション4: 強制インストール（注意して使用）
pip install --break-system-packages SuperClaude
```

**コンポーネント不足:**
```bash
python3 -m SuperClaude install --components core commands agents modes --force
```

### コマンド問題

**コマンドが認識されない:**
1. Claude Codeを完全に再起動
2. 確認: `python3 -m SuperClaude --version`
3. テスト: `/sc:brainstorm "test"`

**エージェントが活性化しない:**
- 特定キーワードを使用: `/sc:implement "セキュアなJWT認証"`
- 手動活性化: `@agent-security "認証コードをレビュー"`

**パフォーマンス低下:**
```bash
/sc:analyze . --no-mcp               # MCPサーバーなしでテスト
/sc:analyze src/ --scope file        # スコープを制限
```

### MCPサーバー問題

**サーバー接続失敗:**
```bash
ls ~/.claude/.claude.json            # 設定の存在を確認
node --version                       # Node.js 16+を確認
SuperClaude install --components mcp --force
```

**APIキーが必要（Magic/Morphllm）:**
```bash
export TWENTYFIRST_API_KEY="your_key"
export MORPH_API_KEY="your_key"
# または使用: /sc:command --no-mcp
```

## 高度診断

**システム分析:**
```bash
SuperClaude install --diagnose
cat ~/.claude/logs/superclaude.log | tail -50
```

**コンポーネント分析:**
```bash
ls -la ~/.claude/                    # インストールファイルを確認
grep -r "@" ~/.claude/CLAUDE.md      # インポートを確認
```

**インストールリセット:**
```bash
SuperClaude backup --create          # まずバックアップ
SuperClaude uninstall
SuperClaude install --fresh
```

## ヘルプを得る

**ドキュメント:**
- [インストールガイド](../Getting-Started/installation.md) - セットアップ問題
- [コマンドガイド](../User-Guide/commands.md) - 使用方法問題

**コミュニティ:**
- [GitHub Issues](https://github.com/SuperClaude-Org/SuperClaude_Framework/issues)
- 含めること: OS、Pythonバージョン、エラーメッセージ、再現手順