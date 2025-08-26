# 変更履歴

SuperClaudeの全ての注目すべき変更がこのファイルに記録されます。

フォーマットは[Keep a Changelog](https://keepachangelog.com/en/1.0.0/)に基づいており、
このプロジェクトは[セマンティックバージョニング](https://semver.org/spec/v2.0.0.html)に従います。

## [未リリース]

## [4.0.8] - 2025-01-23

### 変更点
- PyPIリリース用のバージョンバンプ
- プロジェクトファイル全体でのバージョン参照を更新

### 技術的変更
- PyPI配布用パッケージの準備
- パッケージ構造と依存関係の検証

## [4.0.7] - 2025-01-23

### 追加
- PyPIおよびNPMパッケージの自動更新チェック
- `--no-update-check` フラグで更新チェックをスキップ
- `--auto-update` フラグでプロンプトなしの自動更新
- 環境変数`SUPERCLAUDE_AUTO_UPDATE`のサポート
- 利用可能なバージョンを色付きバナーで表示する更新通知
- 24時間に1回の更新チェック制限
- スマートインストール方法の検出（pip/pipx/npm/yarn）
- 更新チェックタイムスタンプ用のキャッシュファイル（~/.claude/.update_checkと.npm_update_check）

### 修正
- コンポーネント検証でソースコードではなくpipxでインストールされたバージョンを正しく使用

### 技術的変更
- PyPI更新チェックロジック用の`setup/utils/updater.py`を追加
- NPM更新チェックロジック用の`bin/checkUpdate.js`を追加
- メインエントリーポイント（SuperClaude/__main__.pyとbin/cli.js）に更新チェックを統合
- 遅延を避けるため2秒タイムアウトでのノンブロッキング更新チェック

### 変更点
- **破壊的変更**: エージェントシステムを14の専門エージェントに再構築
- **破壊的変更**: コマンドがユーザーカスタムコマンドとの競合を避けるため`/sc:`名前空間を使用
- コマンドが`~/.claude/commands/sc/`サブディレクトリにインストールされるように
- 全21コマンドを更新：`/analyze` → `/sc:analyze`、`/build` → `/sc:build`など
- 古いコマンド場所から新しい`sc/`サブディレクトリへの自動移行
- **破壊的変更**: ドキュメント再編成 - Docs/ディレクトリをGuides/に名前変更

### 追加
- **新エージェント**: 強化された機能を持つ14の専門ドメインエージェント
  - backend-architect.md、devops-architect.md、frontend-architect.md
  - learning-guide.md、performance-engineer.md、python-expert.md
  - quality-engineer.md、refactoring-expert.md、requirements-analyst.md
  - root-cause-analyst.md、security-engineer.md、socratic-mentor.md
- **新モード**: インテリジェントツール選択マインドセット用のMODE_Orchestration.md（合計5つの行動モード）
- **新コマンド**: 機能とコード実装用の`/sc:implement`（v2ユーザーフィードバックに対応）
- **新ファイル**: プロジェクト固有のClaude Code指示用のCLAUDE.md
- 既存コマンドを新しい名前空間に自動的に移動する移行ロジック
- 古い場所と新しい場所の両方を処理する強化されたアンインストーラ
- 改善されたコマンド競合防止
- より良いコマンド組織と発見性
- 包括的なPyPI公開インフラ
- SuperClaude MCP設定中のAPIキー管理

### 削除
- **破壊的変更**: Templates/ディレクトリの削除（レガシーテンプレートが不要）
- **破壊的変更**: レガシーエージェントを削除し強化された14エージェントシステムに置き換え

### 改善
- 簡潔な行動ガイダンス用のモードとMCPドキュメントのリファクタリング
- PyPI公開用の強化されたプロジェクトクリーンアップとgitignore
- アンインストールと更新安全性の強化を実装
- より良いエージェント専門化とドメイン専門知識フォーカス

### 技術詳細
- コマンドは`/sc:analyze`、`/sc:build`、`/sc:improve`などとしてアクセス可能
- 移行は命名競合を防ぎながら既存機能を保持
- インストールプロセスが既存コマンドを自動的に検出し移行
- 全SuperClaudeコマンドを発見するための`/sc:`プレフィックスのタブ補完サポート
- 改善された組織のためにGuides/ディレクトリがDocs/を置き換え

## [4.0.6] - 2025-08-23

### 修正
- コンポーネント検証がsettings.jsonではなく.superclaude-metadata.jsonを正しくチェック（#291）
- 全コンポーネントでバージョン番号を4.0.6に標準化
- 正しいファイル名（architectとspecialist/engineer）をチェックするエージェント検証を修正
- package.jsonのバージョン不整合を修正（4.0.5だった）

### 変更点
- プロジェクト全体でバージョンを4.0.4から4.0.6にバンプ
- 全コンポーネントバージョンが4.0.6で同期
- 一貫性のためのメタデータファイル構造のクリーンアップ

## [4.0.4] - 2025-08-22

### 追加
- **エージェントシステム**: ペルソナに代わる13の専門ドメインエキスパート
- **行動モード**: 異なるワークフロー用の4つのインテリジェントモード（ブレインストーミング、内省、タスク管理、トークン効率）
- **セッションライフサイクル**: Serena MCPでのクロスセッション永続化用の/sc:loadと/sc:save
- **新コマンド**: /sc:brainstorm、/sc:reflect、/sc:save、/sc:select-tool（合計21コマンド）
- **Serena MCP**: セマンティックコード分析とメモリ管理
- **Morphllm MCP**: Fast Apply機能付きのインテリジェントファイル編集
- **コアコンポーネント**: Pythonベースフレームワーク統合（完全に再設計・実装）
- **テンプレート**: 新しいコンポーネント作成用の包括的テンプレート
- **Python-Ultimate-Expert エージェント**: プロダクション対応コード用のマスターPythonアーキテクト

### 変更点
- コマンドを16から21の専門コマンドに拡張
- ペルソナを13の専門エージェントに置き換え
- MCP統合の強化（合計6サーバー）
- トークン効率の改善（Token Efficiency Modeで30-50%削減）
- セッション管理が永続化のためにSerena統合を使用
- より良いモジュール性のためのフレームワーク構造再編成

### 改善
- 多層オーケストレーション（TodoWrite、/task、/spawn、/loop）によるタスク管理
- 8段階検証サイクルによる品質ゲート
- パフォーマンス監視と最適化
- クロスセッションコンテキスト保持
- ORCHESTRATOR.md強化によるインテリジェントルーティング

## [3.0.0] - 2025-07-14

### 追加
- SuperClaude v3.0の初期リリース
- 開発タスク用の15の専門スラッシュコマンド
- スマートペルソナ自動アクティベーションシステム
- MCPサーバー統合（Context7、Sequential、Magic、Playwright）
- 複数インストールプロファイル付きの統一CLIインストーラ
- 包括的ドキュメントとユーザーガイド
- トークン最適化フレームワーク
- タスク管理システム

### 機能
- **コマンド**: analyze、build、cleanup、design、document、estimate、explain、git、improve、index、load、spawn、task、test、troubleshoot
- **ペルソナ**: architect、frontend、backend、analyzer、security、mentor、refactorer、performance、qa、devops、scribe
- **MCPサーバー**: 公式ライブラリドキュメント、複雑な分析、UIコンポーネント、ブラウザ自動化
- **インストール**: コンポーネント選択付きのクイック、最小、開発者プロファイル