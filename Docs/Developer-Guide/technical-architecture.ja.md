# SuperClaude コンテキストアーキテクチャガイド

## 概要

このガイドでは、SuperClaudeのコンテキスト指向設定フレームワークがどのように構造化され、Claude Codeがこれらのコンテキストファイルをどのように解釈して動作を変更するかを説明します。

**重要**: SuperClaudeは実行プロセス、実行レイヤー、パフォーマンスシステムを持つスタンドアロンソフトウェアではありません。これはClaude Codeが特殊化された動作を採用するために読み取る `.md` 指示ファイルのコレクションです。

## 目次

1. [コンテキストファイルアーキテクチャ](#コンテキストファイルアーキテクチャ)
2. [インポートシステム](#インポートシステム)
3. [エージェントコンテキスト構造](#エージェントコンテキスト構造)
4. [コマンドコンテキスト構造](#コマンドコンテキスト構造)
5. [モードコンテキスト構造](#モードコンテキスト構造)
6. [MCPサーバー設定](#mcpサーバー設定)
7. [Claude Codeがコンテキストを読み取る方法](#claude-codeがコンテキストを読み取る方法)
8. [フレームワークの拡張](#フレームワークの拡張)

## コンテキストファイルアーキテクチャ

### ディレクトリ構造

```
~/.claude/ (SuperClaude フレームワークファイルのみ)
├── CLAUDE.md                       # インポート付きメインコンテキストファイル
├── FLAGS.md                        # フラグ定義とトリガー  
├── RULES.md                        # コア動作ルール
├── PRINCIPLES.md                   # ガイド原則
├── ZIG.md                          # Zig言語統合
├── MCP_Context7.md                 # Context7 MCP統合
├── MCP_Magic.md                    # Magic MCP統合
├── MCP_Morphllm.md                 # Morphllm MCP統合
├── MCP_Playwright.md               # Playwright MCP統合
├── MCP_Sequential.md               # Sequential MCP統合
├── MCP_Serena.md                   # Serena MCP統合
├── MCP_Zig.md                      # Zig MCP統合
├── MODE_Brainstorming.md           # 協力的発見モード
├── MODE_Introspection.md           # 透明な推論モード
├── MODE_Orchestration.md           # ツール協調モード
├── MODE_Task_Management.md         # タスクオーケストレーションモード
├── MODE_Token_Efficiency.md        # 圧縮通信モード
├── agents/                         # ドメインスペシャリストコンテキスト（14個）
│   ├── backend-architect.md        # バックエンド専門知識
│   ├── devops-architect.md         # DevOps専門知識
│   ├── frontend-architect.md       # フロントエンド専門知識
│   ├── learning-guide.md           # 教育専門知識
│   ├── performance-engineer.md     # パフォーマンス専門知識
│   ├── python-expert.md            # Python専門知識
│   ├── quality-engineer.md         # 品質保証専門知識
│   ├── refactoring-expert.md       # コード品質専門知識
│   ├── requirements-analyst.md     # 要件専門知識
│   ├── root-cause-analyst.md       # 問題診断専門知識
│   ├── security-engineer.md        # セキュリティ専門知識
│   ├── socratic-mentor.md          # 教育専門知識
│   ├── system-architect.md         # システム設計専門知識
│   └── technical-writer.md         # ドキュメント専門知識
└── commands/                       # ワークフローパターンコンテキスト
    └── sc/                         # SuperClaudeコマンド名前空間（21個）
        ├── analyze.md              # 分析パターン
        ├── brainstorm.md           # 発見パターン
        ├── build.md                # ビルドパターン
        ├── cleanup.md              # クリーンアップパターン
        ├── design.md               # 設計パターン
        ├── document.md             # ドキュメントパターン
        ├── estimate.md             # 見積もりパターン
        ├── explain.md              # 説明パターン
        ├── git.md                  # Gitワークフローパターン
        ├── implement.md            # 実装パターン
        ├── improve.md              # 改善パターン
        ├── index.md                # インデックスパターン
        ├── load.md                 # コンテキスト読み込みパターン
        ├── reflect.md              # 反映パターン
        ├── save.md                 # セッション永続化パターン
        ├── select-tool.md          # ツール選択パターン
        ├── spawn.md                # マルチエージェントパターン
        ├── task.md                 # タスク管理パターン
        ├── test.md                 # テストパターン
        ├── troubleshoot.md         # トラブルシューティングパターン
        └── workflow.md             # ワークフロー計画パターン

注意: 他のディレクトリ（backups/、logs/、projects/、serena/など）は
Claude Code動作ディレクトリであり、SuperClaudeフレームワークコンテンツの一部ではありません。
```

### コンテキストファイル種類

| ファイル種類 | 目的 | 有効化 | 例 |
|-----------|---------|------------|---------|
| **コマンド** | ワークフローパターンを定義 | `/sc:[command]` (コンテキストトリガー) | ユーザーが `/sc:implement` を入力 → `implement.md` を読取 |
| **エージェント** | ドメイン専門知識を提供 | `@agent-[name]` または自動 | `@agent-security` → `security-engineer.md` を読取 |
| **モード** | インタラクションスタイルを変更 | フラグまたはトリガー | `--brainstorm` → ブレインストーミングモード有効化 |
| **コア** | 基本ルールを設定 | 常にアクティブ | `RULES.md` は常に読み込み |

## インポートシステム

### CLAUDE.md の動作方法

メインの `CLAUDE.md` ファイルは複数のコンテキストファイルを読み込むためのインポートシステムを使用します：

```markdown
# CLAUDE

*MANDATORY*
@FLAGS.md                  # フラグ定義とトリガー
@RULES.md                  # コア動作ルール
@PRINCIPLES.md             # ガイド原則
*SECONDARY*
@MCP_Context7.md           # Context7 MCP統合
@MCP_Magic.md              # Magic MCP統合
@MCP_Morphllm.md           # Morphllm MCP統合
@MCP_Playwright.md         # Playwright MCP統合
@MCP_Sequential.md         # Sequential MCP統合
@MCP_Serena.md             # Serena MCP統合
@MCP_Zig.md                # Zig MCP統合
*CRITICAL*
@MODE_Brainstorming.md     # 協力的発見モード
@MODE_Introspection.md     # 透明な推論モード
@MODE_Task_Management.md   # タスクオーケストレーションモード
@MODE_Orchestration.md     # ツール協調モード
@MODE_Token_Efficiency.md  # 圧縮通信モード
*LANGUAGE SPECIFIC*
@ZIG.md                    # Zig言語統合
```

### インポート処理

1. Claude Code が `CLAUDE.md` を読取
2. `@import` ステートメントに遭遇
3. 参照ファイルをコンテキストに読み込み
4. 完全な動作フレームワークを構築
5. ユーザー入力に基づいて関連コンテキストを適用

## エージェントコンテキスト構造

### エージェントファイルの構造

各エージェント `.md` ファイルは以下の構造に従います：

```markdown
---
name: agent-name
description: 簡潔な説明
category: specialized|architecture|quality
tools: Read, Write, Edit, Bash, Grep
---

# エージェント名

## トリガー
- このエージェントを有効化するキーワード
- 有効化をトリガーするファイル種類
- 複雑度閾値

## 動作マインドセット
コア哲学とアプローチ

## 焦点領域
- ドメイン専門知識領域1
- ドメイン専門知識領域2

## 主要アクション
1. 特定の動作パターン
2. 問題解決アプローチ
```

### エージェント有効化ロジック

- **手動**: ユーザーが `@agent-python-expert "task"` と入力
- **自動**: リクエスト内のキーワードがエージェント読み込みをトリガー
- **コンテキスト**: ファイル種類またはパターンが関連エージェントを有効化

## コマンドコンテキスト構造

### コマンドファイルの構造

```markdown
---
name: command-name
description: コマンドの目的
category: utility|orchestration|analysis
complexity: basic|enhanced|advanced
mcp-servers: [context7, sequential]
personas: [architect, engineer]
---

# /sc:command-name

## トリガー
- このコマンドを使用するとき
- コンテキストインジケーター

## 使用方法
/sc:command-name [target] [--options]

## ワークフローパターン
1. ステップ1: 初期アクション
2. ステップ2: 処理
3. ステップ3: 検証

## 例
実用的な使用例
```

### コマンド処理

ユーザーがClaude Code会話で `/sc:implement "feature"` と入力すると：
1. Claude が `commands/sc/implement.md` を読取
2. 実装ワークフローパターンを採用
3. 関連エージェントを自動有効化する可能性
4. 定義されたワークフローステップに従う

## モードコンテキスト構造

### 動作モード

モードはClaudeのインタラクションスタイルを変更します：

```markdown
# MODE_[Name].md

## 有効化トリガー
- フラグ: --mode-name
- キーワード: [triggers]
- 複雑度: threshold

## 動作変更
- コミュニケーションスタイル変更
- 意思決定調整
- 出力形式変更

## インタラクションパターン
- 応答方法
- 優先すべき事項
```

## MCPサーバー設定

### 設定場所

MCPサーバーは `~/.claude.json`（SuperClaudeコンテキストの一部ではない）で設定されます：

```json
{
  "mcpServers": {
    "context7": {
      "command": "npx",
      "args": ["-y", "@upstash/context7-mcp@latest"]
    },
    "sequential-thinking": {
      "command": "npx",
      "args": ["-y", "sequential-thinking-mcp@latest"]
    }
  }
}
```

### MCP統合

- **MCPサーバー**: ツールを提供する実際のソフトウェア
- **SuperClaude**: Claudeにいつ使用するかを教えるコンテキスト
- **有効化**: フラグやキーワードがMCP使用をトリガー

## Claude Codeがコンテキストを読み取る方法

### コンテキスト読み込みシーケンス

```
ユーザー入力（Claude Codeで）: "/sc:analyze src/ --focus security"
                    ↓
1. コマンド解析: 'analyze' コマンドを識別
                    ↓
2. コンテキスト読み込み: commands/sc/analyze.md を読取
                    ↓
3. フラグ確認: --focus security
                    ↓
4. 自動有効化: security-engineer.md を読み込み
                    ↓
5. パターン適用: 分析ワークフローに従う
                    ↓
6. 出力生成: 読み込まれたコンテキストを使用
```

### コンテキスト優先度

1. **明示的コマンド**: `/sc:` コマンドが優先
2. **手動エージェント**: `@agent-` は自動有効化を上書き
3. **フラグ**: コマンド・エージェントの動作を変更
4. **自動有効化**: キーワード・コンテキストに基づく
5. **デフォルト動作**: 標準Claude Code

## フレームワークの拡張

### 新しいコマンドの追加

1. `~/.claude/commands/sc/new-command.md` を作成
2. メタデータ、トリガー、ワークフローを定義
3. コード変更不要 - コンテキストのみ

### 新しいエージェントの追加

1. `~/.claude/agents/new-specialist.md` を作成
2. 専門知識、トリガー、動作を定義
3. エージェントが利用可能に

### 新しいモードの追加

1. `~/.claude/MODE_NewMode.md` を作成
2. 有効化トリガーと変更を定義
3. トリガーに基づいてモード有効化

### ベストプラクティス

- **フォーカスしたコンテキスト**: ファイルごとに1つの概念
- **明確なトリガー**: コンテキストがいつ有効化されるかを定義
- **ワークフローパターン**: ステップバイステップのガイダンスを提供
- **例**: 実用的な使用例を含める
- **メタデータ**: 設定にfrontmatterを使用

## 重要な明確化

### SuperClaudeでないもの

- ❌ **実行エンジンなし**: コードは実行されず、プロセスは実行されません
- ❌ **パフォーマンスシステムなし**: 最適化不可能（単なるテキスト）
- ❌ **検出エンジンなし**: Claude Codeがパターンマッチングを実行
- ❌ **オーケストレーションレイヤーなし**: コンテキストファイルがガイド、制御ではない
- ❌ **品質ゲートなし**: 単なる指示パターン

### SuperClaudeであるもの

- ✅ **コンテキストファイル**: Claude Code用の `.md` 指示
- ✅ **動作パターン**: ワークフローとアプローチ
- ✅ **ドメイン専門知識**: 特殊化された知識コンテキスト
- ✅ **設定**: 実際のツール（MCP）の設定
- ✅ **フレームワーク**: 構造化されたプロンプトエンジニアリング

## まとめ

SuperClaudeのアーキテクチャは意図的にシンプルです：Claude Codeが動作を変更するために読み取る、よく整理されたコンテキストファイルのコレクションです。力は、実行中のコードや実行プロセスからではなく、これらのコンテキストの慎重な作成と体系的な整理から生まれます。

フレームワークの優雅さはそのシンプルさにあります - コンテキストファイルを通じてClaude Codeに構造化された指示を提供することで、ソフトウェアの複雑さなしに洗練された動作変更を実現できます。