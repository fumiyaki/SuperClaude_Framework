# SuperClaude 検証・トラブルシューティングガイド

## 概要

このガイドでは、SuperClaudeインストールの検証方法と、コンテキストファイルと設定のよくある問題のトラブルシューティング方法について説明します。

**重要**: SuperClaudeはコンテキストファイルのコレクションであり、実行可能なソフトウェアではありません。このガイドは、コンテキストファイルが適切にインストールされ、Claude Codeからアクセスできることの検証に焦点を当てています。

## 目次

1. [インストール検証](#インストール検証)
2. [コンテキストファイル検証](#コンテキストファイル検証)
3. [MCPサーバー検証](#mcpサーバー検証)
4. [よくある問題](#よくある問題)
5. [トラブルシューティングコマンド](#トラブルシューティングコマンド)

## インストール検証

### インストール状況確認

```bash
# SuperClaudeインストールシステムが利用可能であることを確認
python3 -m SuperClaude --version
# 期待される結果: SuperClaude Frameworkインストールヘルプ

# Claude Code CLI統合確認
claude --version
# 期待される結果: Claude Codeバージョン情報

# コンテキストファイルがインストールされているか確認
ls ~/.claude/
# 期待される結果: CLAUDE.md、FLAGS.md、RULES.md、agents/、commands/、modes/

# メインコンテキストファイルを確認
head ~/.claude/CLAUDE.md
# 期待される結果: インポート文が表示される
```

### ディレクトリ構造確認

```bash
# すべてのディレクトリが存在することを確認
for dir in agents commands modes; do
    if [ -d ~/.claude/$dir ]; then
        echo "✅ $dir ディレクトリが存在します"
        ls ~/.claude/$dir | wc -l
    else
        echo "❌ $dir ディレクトリが見つかりません"
    fi
done
```

### インストール済みコンポーネント数確認

```bash
# 14のエージェントがある必要があります
ls ~/.claude/agents/*.md | wc -l

# 21のコマンドがある必要があります  
ls ~/.claude/commands/*.md | wc -l

# 5のモードがある必要があります
ls ~/.claude/modes/*.md | wc -l
```

## コンテキストファイル検証

### コアファイル確認

```bash
# コアコンテキストファイルが存在することを確認
for file in CLAUDE.md FLAGS.md RULES.md PRINCIPLES.md; do
    if [ -f ~/.claude/$file ]; then
        echo "✅ $file が存在します ($(wc -l < ~/.claude/$file) 行)"
    else
        echo "❌ $file が見つかりません"
    fi
done
```

### インポートシステム確認

```bash
# CLAUDE.mdに正しいインポートがあることを確認
grep "@import" ~/.claude/CLAUDE.md
# 期待される出力:
# @import commands/*.md
# @import agents/*.md
# @import modes/*.md
# @import FLAGS.md
# @import RULES.md
# @import PRINCIPLES.md
```

### ファイル整合性確認

```bash
# ファイルが読み取り可能なテキストファイルであることを確認
file ~/.claude/CLAUDE.md
# 期待される結果: ASCII text または UTF-8 text

# 破損確認
for file in ~/.claude/**/*.md; do
    if file "$file" | grep -q "text"; then
        echo "✅ $file は有効なテキストです"
    else
        echo "❌ $file が破損している可能性があります"
    fi
done
```

## MCPサーバー検証

### MCP設定確認

```bash
# .claude.jsonが存在することを確認
if [ -f ~/.claude.json ]; then
    echo "✅ MCP設定ファイルが存在します"
    # 設定されているサーバーを確認
    grep -o '"[^"]*":' ~/.claude.json | grep -v mcpServers
else
    echo "❌ MCP設定が見つかりません"
fi
```

### MCPサーバー利用可能性テスト

```bash
# Node.jsが利用可能であることを確認（MCPに必要）
node --version
# 期待される結果: v16.0.0以上

# npxが利用可能であることを確認
npx --version
# 期待される結果: バージョン番号

# Context7 MCP（設定されている場合）をテスト
npx -y @upstash/context7-mcp@latest --help 2>/dev/null && echo "✅ Context7が利用可能" || echo "❌ Context7が利用不可"
```

## よくある問題

### 問題: コマンドが動作しない

**症状**: `/sc:` コンテキストトリガーが期待されるClaude Code動作を生成しない

**検証**:
```bash
# コマンドファイルが存在することを確認
ls ~/.claude/commands/implement.md
# 見つからない場合、SuperClaudeを再インストール

# ファイル内容を確認
head -20 ~/.claude/commands/implement.md
# コマンドメタデータと指示が表示される必要があります
```

**解決法**:
```bash
# commandsコンポーネントを再インストール
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup install --components commands --force
```

### 問題: エージェントが有効化されない

**症状**: `@agent-` 呼び出しがClaude Codeで動作しない

**検証**:
```bash
# すべてのエージェントをリスト表示
ls ~/.claude/agents/

# 特定のエージェントを確認
cat ~/.claude/agents/python-expert.md | head -20
```

**解決法**:
```bash
# エージェントを再インストール
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup install --components agents --force
```

### 問題: コンテキストが読み込まれない

**症状**: Claude CodeがSuperClaudeコンテキストを読み取っていないようだ

**検証**:
```bash
# CLAUDE.mdが正しい場所にあることを確認
ls -la ~/.claude/CLAUDE.md

# Claude Codeがディレクトリにアクセスできることを確認
# Claude Codeでコンテキストが適切に読み込まれているかチェック
```

**解決法**:
1. Claude Codeを再起動
2. プロジェクトディレクトリにいることを確認
3. ファイル権限を確認: `chmod 644 ~/.claude/*.md`

### 問題: MCPサーバーが動作しない

**症状**: MCP機能が利用できない

**検証**:
```bash
# Node.jsインストール確認
which node

# .claude.json構文確認
python3 -c "import json; json.load(open('$HOME/.claude.json'))" && echo "✅ 有効なJSON" || echo "❌ 無効なJSON"
```

**解決法**:
```bash
# Node.jsが見つからない場合はインストール
# Ubuntu: sudo apt install nodejs npm
# macOS: brew install node
# Windows: nodejs.orgからダウンロード

# JSONが無効な場合は修正
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup install --components mcp --force
```

## トラブルシューティングコマンド

### クイック診断

```bash
#!/bin/bash
# SuperClaudeクイック診断スクリプト

echo "=== SuperClaude診断 ==="
echo ""

# インストールシステム確認
echo "1. インストールシステム:"
if command -v SuperClaude &> /dev/null; then
    echo "   ✅ SuperClaudeインストールが利用可能"
    python3 -m SuperClaude --version
else
    echo "   ❌ SuperClaudeが見つかりません - インストール: pipx install SuperClaude (または pip install SuperClaude)"
fi

# コンテキストファイル確認
echo ""
echo "2. コンテキストファイル:"
if [ -d ~/.claude ]; then
    echo "   ✅ ~/.claude ディレクトリが存在します"
    echo "   - エージェント: $(ls ~/.claude/agents/*.md 2>/dev/null | wc -l)"
    echo "   - コマンド: $(ls ~/.claude/commands/*.md 2>/dev/null | wc -l)"
    echo "   - モード: $(ls ~/.claude/modes/*.md 2>/dev/null | wc -l)"
else
    echo "   ❌ ~/.claude ディレクトリが見つかりません"
fi

# MCP確認
echo ""
echo "3. MCP設定:"
if [ -f ~/.claude.json ]; then
    echo "   ✅ MCP設定が存在します"
else
    echo "   ❌ MCP設定がありません"
fi

# Node.js確認
echo ""
echo "4. Node.js（MCP用）:"
if command -v node &> /dev/null; then
    echo "   ✅ Node.jsインストール済み: $(node --version)"
else
    echo "   ⚠️  Node.jsがインストールされていません（オプション、MCPに必要）"
fi

echo ""
echo "=== 診断完了 ==="
```

### ファイル権限修正

```bash
# すべてのコンテキストファイルの権限を修正
chmod 644 ~/.claude/*.md
chmod 644 ~/.claude/**/*.md
chmod 755 ~/.claude ~/.claude/agents ~/.claude/commands ~/.claude/modes
```

### 完全再インストール

```bash
# 既存設定をバックアップ
cp -r ~/.claude ~/.claude.backup.$(date +%Y%m%d)

# 既存インストールを削除
rm -rf ~/.claude

# すべてを再インストール
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup install

# 必要に応じてバックアップからカスタマイズを復元
```

## 重要な注意事項

### 検証しないもの

- **コード実行なし**: コンテキストファイルは実行されないため、ランタイム検証は不要
- **パフォーマンス指標なし**: コードは実行されないため、測定するパフォーマンスはありません
- **単体テストなし**: コンテキストファイルは指示であり、関数ではありません
- **統合テストなし**: Claude Codeがファイルを読み取り、検証は動作的です

### 検証するもの

- **ファイル存在**: コンテキストファイルが正しい場所に存在
- **ファイル整合性**: ファイルが有効なテキストで読み取り可能
- **ディレクトリ構造**: 適切な整理が維持されている
- **設定妥当性**: JSONファイルが構文的に正しい
- **依存関係利用可能**: MCPサーバー用Node.js（オプション）
- **動作テスト**: コンテキストファイルが期待されるClaude Code動作を生成

## まとめ

SuperClaudeの検証は、コンテキストファイルが適切にインストールされ、Claude Codeからアクセス可能であることの確認に焦点を当てています。SuperClaudeはソフトウェアではなく設定フレームワークであるため、検証はファイル存在、整合性、Claude Code会話での動作テストに集中します。