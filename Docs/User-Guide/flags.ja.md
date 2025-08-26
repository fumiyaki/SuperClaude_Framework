# SuperClaudeフラグガイド

**ほとんどのフラグは自動でアクティブ化されます** - Claude Codeはリクエスト内のキーワードやパターンに基づいて適切なコンテキストを関与させるための行動指示を読みます。

## 重要な自動アクティベーションフラグ（90%の使用例）

### コア解析フラグ

| フラグ | アクティブ化されるとき | 何をするか |
|------|---------------|--------------|
| `--think` | 5つ以上のファイルまたは複雑な解析 | 標準構造化解析（約4Kトークン） |
| `--think-hard` | アーキテクチャ解析、システム依存関係 | 拡張ツールを使った深い解析（約10Kトークン） |
| `--ultrathink` | クリティカルシステム再設計、レガシーモダナイゼーション | すべてのツールを使った最大深度解析（約32Kトークン） |

### MCPサーバーフラグ

| フラグ | サーバー | 目的 | 自動トリガー |
|------|---------|---------|---------------|
| `--c7` / `--context7` | Context7 | 公式ドキュメント、フレームワークパターン | ライブラリインポート、フレームワーク質問 |
| `--seq` / `--sequential` | Sequential | マルチステップ推論、デバッグ | 複雑なデバッグ、システム設計 |
| `--magic` | Magic | UIコンポーネント生成 | `/ui`コマンド、フロントエンドキーワード |
| `--play` / `--playwright` | Playwright | ブラウザーテスト、E2E検証 | テストリクエスト、視覚的検証 |
| `--morph` / `--morphllm` | Morphllm | バルク変換、パターン編集 | バルク操作、スタイル強制 |
| `--serena` | Serena | プロジェクトメモリ、シンボル操作 | シンボル操作、大規模コードベース |

### 行動モードフラグ

| フラグ | アクティブ化されるとき | 何をするか |
|------|---------------|--------------|
| `--brainstorm` | 曖昧なリクエスト、探索キーワード | 協力的発見マインドセット |
| `--introspect` | 自己解析、エラー回復 | 透明性を持つ推論プロセスの公開 |
| `--task-manage` | 3つ以上のステップ、複雑なスコープ | 委任によるオーケストレーション |
| `--orchestrate` | マルチツール操作、パフォーマンス要件 | ツール選択と並列実行の最適化 |
| `--token-efficient` / `--uc` | コンテキスト>75%、効率性要件 | シンボル拡張コミュニケーション、30-50%削減 |

### 実行制御フラグ

| フラグ | アクティブ化されるとき | 何をするか |
|------|---------------|--------------|
| `--loop` | 「改善」、「磨く」、「洗練」キーワード | 反復拡張サイクル |
| `--safe-mode` | 本番、>85%リソース使用量 | 最大検証、保守的実行 |
| `--validate` | リスク>0.7、本番環境 | 実行前リスク評価 |
| `--delegate` | >7ディレクトリまたは>50ファイル | サブエージェント並列処理 |

## コマンド固有フラグ

### 解析コマンドフラグ（`/sc:analyze`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--focus` | 特定のドメインをターゲット | `security`, `performance`, `quality`, `architecture` |
| `--depth` | 解析の徹底性 | `quick`, `deep` |
| `--format` | 出力フォーマット | `text`, `json`, `report` |

### ビルドコマンドフラグ（`/sc:build`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | ビルド設定 | `dev`, `prod`, `test` |
| `--clean` | ビルド前にクリーン | Boolean |
| `--optimize` | 最適化を有効 | Boolean |
| `--verbose` | 詳細出力 | Boolean |

### デザインコマンドフラグ（`/sc:design`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | デザインターゲット | `architecture`, `api`, `component`, `database` |
| `--format` | 出力フォーマット | `diagram`, `spec`, `code` |

### 説明コマンドフラグ（`/sc:explain`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--level` | 複雑性レベル | `basic`, `intermediate`, `advanced` |
| `--format` | 説明スタイル | `text`, `examples`, `interactive` |
| `--context` | ドメインコンテキスト | 任意のドメイン（例：`react`, `security`） |

### 改善コマンドフラグ（`/sc:improve`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | 改善フォーカス | `quality`, `performance`, `maintainability`, `style`, `security` |
| `--safe` | 保守的アプローチ | Boolean |
| `--interactive` | ユーザーガイダンス | Boolean |
| `--preview` | 実行せずに表示 | Boolean |

### タスクコマンドフラグ（`/sc:task`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--strategy` | タスクアプローチ | `systematic`, `agile`, `enterprise` |
| `--parallel` | 並列実行 | Boolean |
| `--delegate` | サブエージェント調整 | Boolean |

### ワークフローコマンドフラグ（`/sc:workflow`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--strategy` | ワークフローアプローチ | `systematic`, `agile`, `enterprise` |
| `--depth` | 解析深度 | `shallow`, `normal`, `deep` |
| `--parallel` | 並列調整 | Boolean |

### トラブルシュートコマンドフラグ（`/sc:troubleshoot`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | 問題カテゴリ | `bug`, `build`, `performance`, `deployment` |
| `--trace` | トレース解析を含む | Boolean |
| `--fix` | 修正を適用 | Boolean |

### クリーンアップコマンドフラグ（`/sc:cleanup`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | クリーンアップターゲット | `code`, `imports`, `files`, `all` |
| `--safe` / `--aggressive` | クリーンアップ強度 | Boolean |
| `--interactive` | ユーザーガイダンス | Boolean |
| `--preview` | 実行せずに表示 | Boolean |

### 見積もりコマンドフラグ（`/sc:estimate`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | 見積もりフォーカス | `time`, `effort`, `complexity` |
| `--unit` | 時間単位 | `hours`, `days`, `weeks` |
| `--breakdown` | 詳細な内訳 | Boolean |

### インデックスコマンドフラグ（`/sc:index`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | インデックスターゲット | `docs`, `api`, `structure`, `readme` |
| `--format` | 出力フォーマット | `md`, `json`, `yaml` |

### 反省コマンドフラグ（`/sc:reflect`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--type` | 反省スコープ | `task`, `session`, `completion` |
| `--analyze` | 解析を含む | Boolean |
| `--validate` | 完全性を検証 | Boolean |

### スポーンコマンドフラグ（`/sc:spawn`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--strategy` | 調整アプローチ | `sequential`, `parallel`, `adaptive` |
| `--depth` | 解析深度 | `normal`, `deep` |

### Gitコマンドフラグ（`/sc:git`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--smart-commit` | コミットメッセージ生成 | Boolean |
| `--interactive` | ガイド操作 | Boolean |

### ツール選択コマンドフラグ（`/sc:select-tool`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--analyze` | ツール解析 | Boolean |
| `--explain` | 選択を説明 | Boolean |

### テストコマンドフラグ（`/sc:test`）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--coverage` | カバレッジを含む | Boolean |
| `--type` | テストタイプ | `unit`, `integration`, `e2e` |
| `--watch` | ウォッチモード | Boolean |

## 高度制御フラグ

### スコープとフォーカス

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--scope` | 解析境界 | `file`, `module`, `project`, `system` |
| `--focus` | ドメインターゲティング | `performance`, `security`, `quality`, `architecture`, `accessibility`, `testing` |

### 実行制御

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--concurrency [n]` | 並列操作制御 | 1-15 |
| `--iterations [n]` | 改善サイクル | 1-10 |
| `--all-mcp` | すべてのMCPサーバーを有効 | Boolean |
| `--no-mcp` | ネイティブツールのみ | Boolean |

### システムフラグ（SuperClaudeインストール）

| フラグ | 目的 | 値 |
|------|---------|--------|
| `--verbose` / `-v` | 詳細ログ | Boolean |
| `--quiet` / `-q` | 出力を抑制 | Boolean |
| `--dry-run` | 操作をシミュレート | Boolean |
| `--force` | チェックをスキップ | Boolean |
| `--yes` / `-y` | 自動確認 | Boolean |
| `--install-dir` | ターゲットディレクトリ | パス |
| `--legacy` | レガシースクリプトを使用 | Boolean |
| `--version` | バージョン表示 | Boolean |
| `--help` | ヘルプ表示 | Boolean |

## 一般的な使用パターン

### フロントエンド開発

```bash
/sc:implement "レスポンシブダッシュボード" --magic --c7
/sc:design component-library --type component --format code
/sc:test ui-components/ --magic --play
/sc:improve legacy-ui/ --magic --morph --validate
```

### バックエンド開発

```bash
/sc:analyze api/ --focus performance --seq --think
/sc:design payment-api --type api --format spec
/sc:troubleshoot "APIタイムアウト" --type performance --trace
/sc:improve auth-service --type security --validate
```

### 大規模プロジェクト

```bash
/sc:analyze . --ultrathink --all-mcp --safe-mode
/sc:workflow enterprise-system --strategy enterprise --depth deep
/sc:cleanup . --type all --safe --interactive
/sc:estimate "マイクロサービスに移行" --type complexity --breakdown
```

### 品質 & メンテナンス

```bash
/sc:improve src/ --type quality --safe --interactive
/sc:cleanup imports --type imports --preview
/sc:reflect --type completion --validate
/sc:git commit --smart-commit
```

## フラグの相互作用

### 互換性のある組み合わせ

- `--think` + `--c7`：ドキュメント付き解析
- `--magic` + `--play`：テスト付きUI生成
- `--serena` + `--morph`：変換付きプロジェクトメモリ
- `--safe-mode` + `--validate`：最大安全性
- `--loop` + `--validate`：検証付き反復改善

### 競合するフラグ

- `--all-mcp` vs 個別MCPフラグ（どちらか一方を使用）
- `--no-mcp` vs 任意のMCPフラグ（--no-mcpが優先）
- `--safe` vs `--aggressive`（クリーンアップ強度）
- `--quiet` vs `--verbose`（出力レベル）

### 自動有効化関係

- `--safe-mode`が`--uc`と`--validate`を自動有効化
- `--ultrathink`がすべてのMCPサーバーを自動有効化
- `--think-hard`が`--seq` + `--c7`を自動有効化
- `--magic`がUI重点エージェントをトリガー

## フラグのトラブルシューティング

### よくある問題

- **ツールが多すぎる**：ネイティブツールのみでテストするために`--no-mcp`を使用
- **操作が遅すぎる**：出力を圧縮するために`--uc`を追加
- **検証がブロックされる**：開発では`--safe-mode`の代わりに`--validate`を使用
- **コンテキスト圧迫**：>75%使用時に`--token-efficient`を自動アクティブ化

### デバッグフラグ

```bash
/sc:analyze . --verbose                      # 決定ロジックとフラグアクティベーションを表示
/sc:select-tool "操作" --explain             # ツール選択プロセスを説明
/sc:reflect --type session --analyze         # 現在のセッション決定をレビュー
```

### クイックフィックス

```bash
/sc:analyze . --help                         # コマンドの利用可能フラグを表示
/sc:analyze . --no-mcp                       # ネイティブ実行のみ
/sc:cleanup . --preview                      # クリーンアップされる内容を表示
```

## フラグ優先順位ルール

1. **安全性ファースト**：`--safe-mode` > `--validate` > 最適化フラグ
2. **明示的オーバーライド**：ユーザーフラグ > 自動検出
3. **深度階層**：`--ultrathink` > `--think-hard` > `--think`
4. **MCP制御**：`--no-mcp`がすべての個別MCPフラグをオーバーライド
5. **スコープ優先度**：system > project > module > file

## 関連リソース

- [コマンドガイド](commands.md) - これらのフラグを使用するコマンド
- [MCPサーバーガイド](mcp-servers.md) - MCPフラグアクティベーションの理解
- [セッション管理](session-management.md) - 永続セッションでのフラグ使用