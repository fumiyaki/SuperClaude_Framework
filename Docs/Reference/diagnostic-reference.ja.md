# SuperClaude 診断リファレンスガイド

## 概要

このガイドは、SuperClaudeコンテキストファイルと設定の問題診断手順を提供します。SuperClaudeはテキストファイルの集合体（実行ソフトウェアではない）なので、診断はファイル検証と設定チェックにフォーカスします。

**重要**: 監視すべきプロセス、測定すべきパフォーマンスメトリクス、分析すべきシステムリソースはありません。SuperClaudeは純粋にClaude Codeが読み込む設定ファイルです。

## クイック診断

### ワンライン健全性チェック

```bash
# クイック状態チェック
ls ~/.claude/CLAUDE.md && echo "✅ SuperClaude installed" || echo "❌ Not installed"
```

### 基本診断コマンド

```bash
# SuperClaudeがインストールされているかチェック
python3 -m SuperClaude --version

# コンテキストファイル数をカウント
find ~/.claude -name "*.md" -type f | wc -l
# 期待値: 40+ファイル

# ファイルサイズをチェック（コンテキストファイルは内容を持つべき）
find ~/.claude -name "*.md" -type f -size 0
# 期待値: 出力なし（空ファイルなし）

# ディレクトリ構造を確認
tree -L 2 ~/.claude/
# またはtreeコマンドがない場合:
ls -la ~/.claude/
```

## ファイルシステム診断

### コンテキストファイル検証

```bash
#!/bin/bash
# 包括的コンテキストファイルチェック

echo "=== SuperClaude コンテキストファイル診断 ==="

# 期待数を定義
EXPECTED_AGENTS=14
EXPECTED_COMMANDS=21
EXPECTED_MODES=6

# 実際のファイル数をカウント
ACTUAL_AGENTS=$(ls ~/.claude/agents/*.md 2>/dev/null | wc -l)
ACTUAL_COMMANDS=$(ls ~/.claude/commands/*.md 2>/dev/null | wc -l)
ACTUAL_MODES=$(ls ~/.claude/modes/*.md 2>/dev/null | wc -l)

# 結果を報告
echo "エージェント: $ACTUAL_AGENTS/$EXPECTED_AGENTS $([ $ACTUAL_AGENTS -ge $EXPECTED_AGENTS ] && echo ✅ || echo ⚠️)"
echo "コマンド: $ACTUAL_COMMANDS/$EXPECTED_COMMANDS $([ $ACTUAL_COMMANDS -ge $EXPECTED_COMMANDS ] && echo ✅ || echo ⚠️)"
echo "モード: $ACTUAL_MODES/$EXPECTED_MODES $([ $ACTUAL_MODES -ge $EXPECTED_MODES ] && echo ✅ || echo ⚠️)"

# コアファイルをチェック
for file in CLAUDE.md FLAGS.md RULES.md PRINCIPLES.md; do
    if [ -f ~/.claude/$file ]; then
        SIZE=$(wc -c < ~/.claude/$file)
        echo "$file: $SIZE bytes ✅"
    else
        echo "$file: 不足 ❌"
    fi
done
```

### インポートシステムチェック

```bash
# CLAUDE.mdのインポート文を確認
echo "=== インポートシステムチェック ==="
if [ -f ~/.claude/CLAUDE.md ]; then
    echo "CLAUDE.mdで見つかったインポート:"
    grep "^@import" ~/.claude/CLAUDE.md
    
    # インポート文をカウント
    IMPORT_COUNT=$(grep -c "^@import" ~/.claude/CLAUDE.md)
    echo "総インポート数: $IMPORT_COUNT"
    
    if [ $IMPORT_COUNT -ge 5 ]; then
        echo "✅ インポートシステムが正しく設定されています"
    else
        echo "⚠️ 一部のインポートが不足している可能性があります"
    fi
else
    echo "❌ CLAUDE.mdが見つかりません"
fi
```

## 設定診断

### MCPサーバー設定チェック

```bash
# MCP設定をチェック
echo "=== MCP設定診断 ==="

CONFIG_FILE=~/.claude.json

if [ -f "$CONFIG_FILE" ]; then
    echo "✅ 設定ファイルが存在します"
    
    # JSON構文を検証
    if python3 -c "import json; json.load(open('$CONFIG_FILE'))" 2>/dev/null; then
        echo "✅ 有効なJSON構文"
        
        # 設定されたサーバーをリスト表示
        echo "設定されたMCPサーバー:"
        python3 -c "
import json
with open('$HOME/.claude.json') as f:
    config = json.load(f)
    if 'mcpServers' in config:
        for server in config['mcpServers']:
            print(f'  - {server}')
    else:
        print('  サーバーが設定されていません')
        "
    else
        echo "❌ $CONFIG_FILEのJSON構文が無効です"
    fi
else
    echo "⚠️ MCP設定ファイルが見つかりません"
    echo "  MCPサーバーを使用しない場合は問題ありません"
fi
```

### 権限診断

```bash
# ファイル権限をチェック
echo "=== ファイル権限チェック ==="

# ファイルが読み取り可能かチェック
UNREADABLE_COUNT=0
for file in ~/.claude/**/*.md; do
    if [ ! -r "$file" ]; then
        echo "❌ 読み取り不可: $file"
        ((UNREADABLE_COUNT++))
    fi
done

if [ $UNREADABLE_COUNT -eq 0 ]; then
    echo "✅ すべてのコンテキストファイルが読み取り可能です"
else
    echo "⚠️ 読み取り不可なファイルが$UNREADABLE_COUNT個見つかりました"
    echo "修正方法: chmod 644 ~/.claude/**/*.md"
fi

# ディレクトリ権限をチェック
for dir in ~/.claude ~/.claude/agents ~/.claude/commands ~/.claude/modes; do
    if [ -d "$dir" ]; then
        if [ -x "$dir" ]; then
            echo "✅ $dirにアクセス可能"
        else
            echo "❌ $dirにアクセス不可"
        fi
    else
        echo "❌ $dirが存在しません"
    fi
done
```

## 一般的な問題診断

### 問題: コマンドが認識されない

```bash
# コマンド問題を診断
COMMAND="implement"  # 異なるコマンドをテストするために変更

echo "=== コマンド診断: $COMMAND ==="

FILE=~/.claude/commands/$COMMAND.md

if [ -f "$FILE" ]; then
    echo "✅ コマンドファイルが存在します"
    
    # ファイルサイズをチェック
    SIZE=$(wc -c < "$FILE")
    if [ $SIZE -gt 100 ]; then
        echo "✅ ファイルに内容があります ($SIZE bytes)"
    else
        echo "⚠️ ファイルが小さすぎるようです ($SIZE bytes)"
    fi
    
    # メタデータをチェック
    if head -10 "$FILE" | grep -q "^---"; then
        echo "✅ メタデータヘッダーがあります"
    else
        echo "⚠️ メタデータヘッダーが不足しています"
    fi
    
    # コマンドパターンをチェック
    if grep -q "/sc:$COMMAND" "$FILE"; then
        echo "✅ コマンドパターンを含んでいます"
    else
        echo "⚠️ コマンドパターンが不足しています"
    fi
else
    echo "❌ コマンドファイルが見つかりません: $FILE"
    echo "利用可能なコマンド:"
    ls ~/.claude/commands/ | sed 's/.md$//'
fi
```

### 問題: エージェントが活性化しない

```bash
# エージェント問題を診断
AGENT="python-expert"  # 異なるエージェントをテストするために変更

echo "=== エージェント診断: $AGENT ==="

FILE=~/.claude/agents/$AGENT.md

if [ -f "$FILE" ]; then
    echo "✅ エージェントファイルが存在します"
    
    # トリガーキーワードをチェック
    echo "見つかったトリガーキーワード:"
    grep -A 5 "## Triggers" "$FILE" | tail -n +2
    
    # メタデータをチェック
    if head -10 "$FILE" | grep -q "^name:"; then
        echo "✅ メタデータがあります"
    else
        echo "⚠️ メタデータが不足しています"
    fi
else
    echo "❌ エージェントファイルが見つかりません: $FILE"
    echo "利用可能なエージェント:"
    ls ~/.claude/agents/ | sed 's/.md$//'
fi
```

## インストール修復

### クイック修正スクリプト

```bash
#!/bin/bash
# SuperClaude クイック修正スクリプト

echo "=== SuperClaude クイック修正 ==="

# 一般的な問題をチェックして修正
ISSUES_FOUND=0

# 権限を修正
echo "ファイル権限を修正中..."
chmod 644 ~/.claude/*.md 2>/dev/null
chmod 644 ~/.claude/**/*.md 2>/dev/null
chmod 755 ~/.claude ~/.claude/agents ~/.claude/commands ~/.claude/modes 2>/dev/null

# 不足ディレクトリをチェック
for dir in agents commands modes; do
    if [ ! -d ~/.claude/$dir ]; then
        echo "⚠️ 不足ディレクトリ: $dir"
        echo "  実行: SuperClaude install --components $dir"
        ((ISSUES_FOUND++))
    fi
done

# 空ファイルをチェック
EMPTY_FILES=$(find ~/.claude -name "*.md" -type f -size 0 2>/dev/null)
if [ -n "$EMPTY_FILES" ]; then
    echo "⚠️ 空ファイルが見つかりました:"
    echo "$EMPTY_FILES"
    echo "  実行: SuperClaude install --force"
    ((ISSUES_FOUND++))
fi

if [ $ISSUES_FOUND -eq 0 ]; then
    echo "✅ 問題は見つかりませんでした"
else
    echo "$ISSUES_FOUND個の問題が見つかりました - 上記の推奨事項を参照してください"
fi
```

### 完全再インストール

```bash
# 完全クリーン再インストール
echo "=== クリーン再インストール ==="

# 現在のインストールをバックアップ
BACKUP_DIR=~/.claude.backup.$(date +%Y%m%d_%H%M%S)
if [ -d ~/.claude ]; then
    cp -r ~/.claude "$BACKUP_DIR"
    echo "✅ $BACKUP_DIRにバックアップしました"
fi

# 現在のインストールを削除
rm -rf ~/.claude

# 再インストール
SuperClaude install

# インストールを確認
if [ -f ~/.claude/CLAUDE.md ]; then
    echo "✅ 再インストール成功"
else
    echo "❌ 再インストール失敗"
    echo "バックアップを復元中..."
    cp -r "$BACKUP_DIR" ~/.claude
fi
```

## これらの診断が行わないこと

### 適用外の概念

- **CPU/メモリ監視**: 監視すべきプロセスなし
- **パフォーマンスメトリクス**: 測定すべきコード実行なし
- **ネットワーク分析**: ネットワーク操作なし（MCPを除く）
- **プロセス管理**: 実行中のプロセスなし
- **リソース最適化**: 消費されるリソースなし
- **実行タイミング**: 実行されるコードなし

### 重要なことにフォーカス

- **ファイル存在**: コンテキストファイルがインストールされているか？
- **ファイル完全性**: ファイルが読み取り可能で完全か？
- **設定有効性**: JSON構文が正しいか？
- **ディレクトリ構造**: 組織化が正しいか？
- **権限**: Claude Codeがファイルを読み取れるか？

## まとめ

SuperClaude診断はシンプルです: ファイルが存在するか確認し、読み取り可能かチェックし、設定が有効であることを確保します。Claude Codeが読み込むテキストファイルだけなので、複雑なシステム監視やパフォーマンス分析は不要です。ファイルが存在し読み取り可能であれば、SuperClaudeは動作します。