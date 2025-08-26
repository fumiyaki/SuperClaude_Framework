# SuperClaudeコマンドガイド

SuperClaudeはClaude Code用に21のコマンドを提供：ワークフロー用の`/sc:*`コマンドと専門家用の`@agent-*`。

## コマンドタイプ

| タイプ | 使用場所 | フォーマット | 例 |
|------|------------|--------|---------|
| **スラッシュコマンド** | Claude Code | `/sc:[command]` | `/sc:implement "機能"` |
| **エージェント** | Claude Code | `@agent-[name]` | `@agent-security "レビュー"` |
| **インストール** | ターミナル | `SuperClaude [command]` | `SuperClaude install` |

## クイックテスト

```bash
# ターミナル：インストール確認
python3 -m SuperClaude --version
# Claude Code CLI確認：claude --version

# Claude Code：コマンドテスト
/sc:brainstorm "テストプロジェクト"    # 発見質問を開始するはず
/sc:analyze README.md           # 分析を提供するはず
```

**ワークフロー**：`/sc:brainstorm "アイデア"` → `/sc:implement "機能"` → `/sc:test`

## SuperClaudeコマンドの理解

## SuperClaudeの仕組み

SuperClaudeは、Claude Codeが読み取って専門的な動作を採用する行動コンテキストファイルを提供します。`/sc:implement`と入力すると、Claude Codeは`implement.md`コンテキストファイルを読み、その行動指示に従います。

**SuperClaudeコマンドはソフトウェアによって実行されません** - フレームワークから専門指示ファイルを読み込むことでClaude Codeの動作を修正するコンテキストトリガーです。

### コマンドタイプ：

- **スラッシュコマンド** (`/sc:*`)：ワークフローパターンと行動モードをトリガー
- **エージェント呼び出し** (`@agent-*`)：特定のドメイン専門家を手動でアクティブ化
- **フラグ** (`--think`, `--safe-mode`)：コマンドの動作と深度を修正

### コンテキストメカニズム：

1. **ユーザー入力**：`/sc:implement "認証システム"`と入力
2. **コンテキスト読み込み**：Claude Codeが`~/.claude/SuperClaude/Commands/implement.md`を読み込み
3. **動作採用**：Claudeがドメイン専門知識、ツール選択、検証パターンを適用
4. **拡張出力**：セキュリティ考慮とベストプラクティスを含む構造化実装

**キーポイント**：これにより、従来のソフトウェア実行ではなく、コンテキスト管理を通じて洗練された開発ワークフローが作成されます。

### インストール vs 使用コマンド

**ターミナルコマンド** (実際のCLIソフトウェア)：
- `SuperClaude install` - フレームワークコンポーネントをインストール
- `SuperClaude update` - 既存インストールをアップデート
- `SuperClaude uninstall` - フレームワークインストールを削除
- `python3 -m SuperClaude --version` - インストール状況をチェック

**Claude Codeコマンド** (コンテキストトリガー)：
- `/sc:brainstorm` - 要件発見コンテキストをアクティブ化
- `/sc:implement` - 機能開発コンテキストをアクティブ化
- `@agent-security` - セキュリティ専門家コンテキストをアクティブ化
- すべてのコマンドはClaude Codeチャットインターフェース内でのみ動作

> **クイックスタート**：`/sc:brainstorm "あなたのプロジェクトアイデア"` → `/sc:implement "機能名"` → `/sc:test`でコアワークフローを体験してください。

## セットアップのテスト

### ターミナル確認（ターミナル/CMDで実行）

```bash
# SuperClaudeが動作することを確認（主要方法）
python3 -m SuperClaude --version
# 例の出力：SuperClaude 4.0.8

# Claude Code CLIバージョンチェック
claude --version

# インストールされたコンポーネントをチェック
python3 -m SuperClaude install --list-components | grep mcp
# 例の出力：インストールされたMCPコンポーネントを表示
```

### Claude Codeテスト（Claude Codeチャットで入力）

```
# 基本的な/sc:コマンドをテスト
/sc:brainstorm "テストプロジェクト"
# 期待する動作：インタラクティブな要件発見が開始

# コマンドヘルプをテスト
/sc:help
# 期待する動作：利用可能なコマンドのリスト
```

**テストが失敗した場合**：[インストールガイド](../Getting-Started/installation.md)または[トラブルシューティング](#troubleshooting)を確認してください

### コマンドクイックリファレンス

| コマンドタイプ | 実行場所 | フォーマット | 目的 | 例 |
|-------------|--------------|--------|---------|----------|
| **インストール** | ターミナル/CMD | `SuperClaude [command]` | セットアップとメンテナンス | `SuperClaude install` |
| **設定** | ターミナル/CMD | `python3 -m SuperClaude [command]` | 高度な設定 | `python3 -m SuperClaude --version` |
| **スラッシュコマンド** | Claude Code | `/sc:[command]` | ワークフロー自動化 | `/sc:implement "機能"` |
| **エージェント呼び出し** | Claude Code | `@agent-[name]` | 手動専門家アクティベーション | `@agent-security "レビュー"` |
| **拡張フラグ** | Claude Code | `/sc:[command] --flags` | 動作修正 | `/sc:analyze --think-hard` |

> **覚えておいて**：すべての`/sc:`コマンドと`@agent-`呼び出しは、ターミナルではなくClaude Codeチャット内で動作します。これらはClaude CodeがSuperClaudeフレームワークから特定のコンテキストファイルを読み取るトリガーです。

## 目次

- [必須コマンド](#essential-commands) - ここから始める（8つのコアコマンド）
- [一般的なワークフロー](#common-workflows) - 動作するコマンドの組み合わせ
- [完全コマンドリファレンス](#full-command-reference) - カテゴリ別に整理された全21コマンド
- [トラブルシューティング](#troubleshooting) - よくある問題と解決策
- [コマンドインデックス](#command-index) - カテゴリ別コマンド検索

---

## 必須コマンド

**即座の生産性のためのコアワークフローコマンド：**

### `/sc:brainstorm` - プロジェクト発見

**目的**：インタラクティブな要件発見とプロジェクト計画
**構文**：`/sc:brainstorm "あなたのアイデア"` `[--strategy systematic|creative]`

**使用例**：
- 新プロジェクト計画：`/sc:brainstorm "Eコマースプラットフォーム"`
- 機能探索：`/sc:brainstorm "ユーザー認証システム"`
- 問題解決：`/sc:brainstorm "遅いデータベースクエリ"`

### `/sc:implement` - 機能開発

**目的**：インテリジェント専門家ルーティングによるフルスタック機能実装
**構文**：`/sc:implement "機能説明"` `[--type frontend|backend|fullstack] [--focus security|performance]`

**使用例**：
- 認証：`/sc:implement "JWTログインシステム"`
- UIコンポーネント：`/sc:implement "レスポンシブダッシュボード"`
- API：`/sc:implement "RESTユーザーエンドポイント"`
- データベース：`/sc:implement "リレーション付きユーザースキーマ"`

### `/sc:analyze` - コード評価

**目的**：品質、セキュリティ、パフォーマンスにわたる包括的コード解析
**構文**：`/sc:analyze [path]` `[--focus quality|security|performance|architecture]`

**使用例**：
- プロジェクトヘルス：`/sc:analyze .`
- セキュリティ監査：`/sc:analyze --focus security`
- パフォーマンスレビュー：`/sc:analyze --focus performance`

### `/sc:troubleshoot` - 問題診断

**目的**：ルートコース解析による系統的問題診断
**構文**：`/sc:troubleshoot "問題説明"` `[--type build|runtime|performance]`

**使用例**：
- ランタイムエラー：`/sc:troubleshoot "ログインで500エラー"`
- ビルド失敗：`/sc:troubleshoot --type build`
- パフォーマンス問題：`/sc:troubleshoot "遅いページ読み込み"`

### `/sc:test` - 品質保証

**目的**：カバレッジ解析による包括的テスト
**構文**：`/sc:test` `[--type unit|integration|e2e] [--coverage] [--fix]`

**使用例**：
- 完全テストスイート：`/sc:test --coverage`
- ユニットテスト：`/sc:test --type unit --watch`
- E2E検証：`/sc:test --type e2e`

### `/sc:improve` - コード拡張

**目的**：系統的コード改善と最適化を適用
**構文**：`/sc:improve [path]` `[--type performance|quality|security] [--preview]`

**使用例**：
- 一般改善：`/sc:improve src/`
- パフォーマンス最適化：`/sc:improve --type performance`
- セキュリティ強化：`/sc:improve --type security`

### `/sc:document` - ドキュメント生成

**目的**：コードとAPIの包括的ドキュメント生成
**構文**：`/sc:document [path]` `[--type api|user-guide|technical] [--format markdown|html]`

**使用例**：
- APIドキュメント：`/sc:document --type api`
- ユーザーガイド：`/sc:document --type user-guide`
- 技術ドキュメント：`/sc:document --type technical`

### `/sc:workflow` - 実装計画

**目的**：要件から構造化実装計画を生成
**構文**：`/sc:workflow "機能説明"` `[--strategy agile|waterfall] [--format markdown]`

**使用例**：
- 機能計画：`/sc:workflow "ユーザー認証"`
- スプリント計画：`/sc:workflow --strategy agile`
- アーキテクチャ計画：`/sc:workflow "マイクロサービス移行"`

---

## 一般的なワークフロー

**実証済みのコマンドの組み合わせ：**

### 新プロジェクトセットアップ

```bash
/sc:brainstorm "プロジェクト概念"      # 要件定義
/sc:design "システムアーキテクチャ"      # 技術設計作成
/sc:workflow "実装計画"              # 開発ロードマップ生成
```

### 機能開発

```bash
/sc:implement "機能名"               # 機能を構築
/sc:test --coverage                 # テストで検証
/sc:document --type api             # ドキュメント生成
```

### コード品質改善

```bash
/sc:analyze --focus quality          # 現状評価
/sc:improve --preview               # 改善をプレビュー
/sc:test --coverage                 # 変更を検証
```

### バグ調査

```bash
/sc:troubleshoot "問題説明"          # 問題を診断
/sc:analyze --focus problem-area    # 深い解析
/sc:improve --fix --safe-mode       # ターゲット修正を適用
```

## 完全コマンドリファレンス

### 開発コマンド

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **workflow** | 実装計画 | プロジェクトロードマップ、スプリント計画 |
| **implement** | 機能開発 | フルスタック機能、API開発 |
| **build** | プロジェクトコンパイル | CI/CD、本番ビルド |
| **design** | システムアーキテクチャ | API仕様、データベーススキーマ |

### 解析コマンド

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **analyze** | コード評価 | 品質監査、セキュリティレビュー |
| **troubleshoot** | 問題診断 | バグ調査、パフォーマンス問題 |
| **explain** | コード説明 | 学習、コードレビュー |

### 品質コマンド

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **improve** | コード拡張 | パフォーマンス最適化、リファクタリング |
| **cleanup** | 技術負債 | デッドコード削除、整理 |
| **test** | 品質保証 | テスト自動化、カバレッジ解析 |
| **document** | ドキュメント | APIドキュメント、ユーザーガイド |

### プロジェクト管理

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **estimate** | プロジェクト見積 | タイムライン計画、リソース配分 |
| **task** | タスク管理 | 複雑なワークフロー、タスクトラッキング |
| **spawn** | メタオーケストレーション | 大規模プロジェクト、並列実行 |

### ユーティリティコマンド

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **git** | バージョン管理 | コミット管理、ブランチ戦略 |
| **index** | コマンド発見 | 能力探索、コマンド検索 |

### セッションコマンド

| コマンド | 目的 | 最適な用途 |
|---------|---------|----------|
| **load** | コンテキスト読み込み | セッション初期化、プロジェクトオンボーディング |
| **save** | セッション永続化 | チェックポイント、コンテキスト保存 |
| **reflect** | タスク検証 | 進捗評価、完了検証 |
| **select-tool** | ツール最適化 | パフォーマンス最適化、ツール選択 |

---

## コマンドインデックス

**機能別：**
- **計画**：brainstorm、design、workflow、estimate
- **開発**：implement、build、git
- **解析**：analyze、troubleshoot、explain
- **品質**：improve、cleanup、test、document
- **管理**：task、spawn、load、save、reflect
- **ユーティリティ**：index、select-tool

**複雑性別：**
- **初級**：brainstorm、implement、analyze、test
- **中級**：workflow、design、improve、document
- **上級**：spawn、task、select-tool、reflect

## トラブルシューティング

**コマンド問題：**
- **コマンドが見つからない**：インストールを確認：`python3 -m SuperClaude --version`
- **応答なし**：Claude Codeセッションを再起動
- **処理遅延**：MCPサーバーなしでテストするために`--no-mcp`を使用

**クイックフィックス：**
- セッションリセット：`/sc:load`で再初期化
- ステータスチェック：`SuperClaude install --list-components`
- ヘルプを取得：[トラブルシューティングガイド](../Reference/troubleshooting.md)

## 次のステップ

- [フラグガイド](flags.md) - コマンド動作の制御
- [エージェントガイド](agents.md) - 専門家アクティベーション
- [例クックブック](../Reference/examples-cookbook.md) - 実際の使用パターン