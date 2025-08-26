# SuperClaude 統合パターンコレクション

**ステータス**: ✅ **ステータス: 最新** - フレームワーク統合とツール協調のためのコンテキストパターン。

**コンテキスト統合ガイド**: 異なるフレームワークやツールでSuperClaudeコマンドを効果的に使用するためのパターン。覚えておくこと: SuperClaudeはClaude Codeにコンテキストを提供します - 実際の作業はすべてClaudeが行います。

## 概要と使用ガイド

**目的**: 様々な開発フレームワークとツールでSuperClaudeコンテキストを使用するための効果的パターン。

**これは何か**: 特定技術に効果的なコマンド組み合わせとフラグパターン
**これは何でないか**: パフォーマンス最適化や並列実行（コード実行なし）

**主要原則**: SuperClaudeはClaude Codeに何をすべきか、どのように考えるべきかを伝えます。実際の作業はClaude Codeが行います。

## フレームワークコンテキストパターン

### React開発パターン

```bash
# 適切なコンテキストでのReact開発
/sc:implement "TypeScript付きReact 18アプリケーション" --c7
# Context7 MCPは利用可能な場合Reactドキュメントを提供可能
# Magic MCPは設定されている場合UIコンポーネントを支援可能

# 実際に起こること:
# 1. Claudeが実装パターンのためにimplement.mdを読む
# 2. --c7フラグがドキュメントのためにContext7 MCPの使用を提案
# 3. Claudeがこれらのコンテキストに基づいてReactコードを生成

# コンポーネント開発パターン
@agent-frontend-architect "コンポーネントアーキテクチャを設計"
/sc:implement "再利用可能コンポーネントライブラリ"

# React用テストパターン
/sc:test --focus react
# ClaudeがReact Testing Libraryパターンを提案
```

### Node.jsバックエンドパターン

```bash
# Node.jsバックエンド開発パターン
/sc:implement "TypeScript付きExpress.js API" --c7
# ClaudeがNode.jsパターンに従ってExpress APIを作成

# これが意味すること:
# - Claudeがバックエンドパターンに関するコンテキストを読む
# - 適切なミドルウェアと構造を提案
# - コードの実行や最適化はしない

# データベース統合パターン
/sc:implement "Prismaでのデータベースモデル"
@agent-backend-architect "データベーススキーマをレビュー"

# APIテストパターン
/sc:test --focus api
# ClaudeがAPIテストアプローチを提案
```

### Python開発パターン

```bash
# Python Web開発
/sc:implement "FastAPIアプリケーション" --c7
@agent-python-expert "実装をレビュー"

# 起こること:
# - ClaudeがPython固有のコンテキストを使用
# - コンテキストからのFastAPIパターンに従う
# - コードを生成（実行はしない）

# データサイエンスコンテキスト
/sc:implement "データ分析パイプライン"
@agent-python-expert "pandas操作を最適化"
# Claudeが最適化提案を提供（実際の最適化ではない）

# テストパターン
/sc:test --focus python
# Claudeがpytestパターンを提案
```

### フルスタック開発パターン

```bash
# フルスタックアプリケーションパターン
/sc:brainstorm "フルスタックアプリケーションアーキテクチャ"
@agent-system-architect "システムコンポーネントを設計"

# フロントエンド実装
/sc:implement "TypeScript付きReactフロントエンド"
@agent-frontend-architect "コンポーネント構造をレビュー"

# バックエンド実装
/sc:implement "認証付きNode.js API"
@agent-backend-architect "API設計をレビュー"

# 統合
/sc:implement "フロントエンドをバックエンドAPIに接続"
```

## ツール協調パターン

### MCPサーバーの効果的使用

```bash
# ドキュメント用Context7
/sc:explain "Reactフック" --c7
# Context7が設定されている場合、Reactドキュメントを取得可能

# 複雑な推論用Sequential
/sc:troubleshoot "複雑なバグ" --seq
# Sequential MCPが構造化問題解決を支援

# UIコンポーネント用Magic
/sc:implement "UIコンポーネント" --magic
# Magic MCPがモダンUIパターン生成を支援可能

# シンプルなタスクにはMCPなし
/sc:implement "ユーティリティ関数" --no-mcp
# Claudeの組み込み知識のみを使用
```

### エージェントとコマンドの組み合わせ

```bash
# セキュリティ重視開発
@agent-security "認証要件をレビュー"
/sc:implement "セキュア認証システム"
/sc:analyze --focus security

# 品質重視ワークフロー
/sc:implement "新機能"
@agent-quality-engineer "コード品質をレビュー"
/sc:test --focus quality

# アーキテクチャ重視アプローチ
@agent-system-architect "マイクロサービスを設計"
/sc:design "サービス境界"
/sc:implement "サービス通信"
```

## 一般的な統合パターン

### API開発パターン

```bash
# ステップ1: 設計
/sc:design "REST API構造"

# ステップ2: 実装
/sc:implement "検証付きAPIエンドポイント"

# ステップ3: ドキュメント化
/sc:document --type api

# ステップ4: テスト
/sc:test --focus api
```

### データベース統合パターン

```bash
# スキーマ設計
@agent-backend-architect "データベーススキーマを設計"

# モデル実装
/sc:implement "データベースモデル"

# マイグレーション作成
/sc:implement "データベースマイグレーション"

# クエリ最適化提案
@agent-backend-architect "クエリ最適化を提案"
# 注意: Claudeが最適化を提案、実際の最適化はしない
```

### テスト戦略パターン

```bash
# テスト計画
/sc:design "テスト戦略"

# ユニットテスト
/sc:test --type unit

# 統合テスト
/sc:test --type integration

# E2Eテスト提案
/sc:test --type e2e
# Claudeがテストコードを提供、実行はしない
```

## 技術固有パターン

### React + TypeScriptパターン

```bash
# プロジェクト設定ガイダンス
/sc:implement "React TypeScriptプロジェクト構造"

# コンポーネント開発
/sc:implement "props検証付きTypeScript Reactコンポーネント"

# 状態管理
@agent-frontend-architect "状態管理アプローチを推奨"
/sc:implement "Zustand/Reduxでの状態管理"

# テスト
/sc:test --focus react --type unit
```

### Python FastAPIパターン

```bash
# API構造
/sc:implement "FastAPIプロジェクト構造"

# エンドポイント開発
@agent-python-expert "非同期エンドポイントを実装"

# データベース統合
/sc:implement "AlembicでのSQLAlchemyモデル"

# テスト
/sc:test --focus python --type integration
```

### Node.jsマイクロサービスパターン

```bash
# アーキテクチャ設計
@agent-system-architect "マイクロサービスアーキテクチャを設計"

# サービス実装
/sc:implement "Expressでのユーザーサービス"
/sc:implement "JWTでの認証サービス"

# サービス間通信
/sc:implement "サービス通信パターン"

# テストアプローチ
/sc:test --focus microservices
```

## トラブルシューティングパターン

### デバッグワークフロー

```bash
# 問題分析
/sc:troubleshoot "問題を説明"

# 根本原因調査
@agent-root-cause-analyst "症状を分析"

# ソリューション実装
/sc:implement "分析に基づく修正"

# 検証
/sc:test --validate
```

### コードレビューパターン

```bash
# コード分析
/sc:analyze code/ --focus quality

# セキュリティレビュー
@agent-security "脆弱性をレビュー"

# パフォーマンスレビュー
@agent-performance-engineer "改善を提案"
# 注意: 提案のみ、実際のパフォーマンス測定はなし

# 改善実装
/sc:improve code/ --fix
```

## 重要な明確化

### これらのパターンが行うこと

- ✅ 開発タスクへの構造化アプローチを提供
- ✅ コマンドとエージェントを効果的に組み合わせ
- ✅ 適切なツールとフレームワークを提案
- ✅ Claudeがより良いコードを生成するよう導く

### これらのパターンが行わないこと

- ❌ コードを実行またはパフォーマンスを測定
- ❌ テストを実行またはアプリケーションをデプロイ
- ❌ 実際の実行速度を最適化
- ❌ 実際の監視やメトリクスを提供
- ❌ 並列プロセスを調整（すべてが順次テキスト）

## ベストプラクティス

### 効果的パターン使用

1. **コンテキストから開始**: プロジェクト理解を確立するために`/sc:load`を使用
2. **専門知識をレイヤー化**: 一般的コマンドと特定エージェントを組み合わせ
3. **適切にフォーカス**: 的を絞った結果のために`--focus`フラグを使用
4. **スコープを管理**: 全コードベースではなく特定モジュールで作業
5. **決定を文書化**: サマリー作成のために`/sc:save`を使用

### パターン選択

- **シンプルタスク**: MCPなしで基本コマンドを使用
- **複雑タスク**: 適切なエージェントとMCPサーバーを追加
- **セキュリティ重要**: 常に`@agent-security`を含める
- **UI開発**: 設定されている場合`--magic`フラグを検討
- **ドキュメントニーズ**: フレームワークドキュメント用に`--c7`を使用

## まとめ

これらの統合パターンは、異なる開発シナリオでSuperClaudeコマンド、エージェント、フラグを効果的に組み合わせる方法を示しています。すべてのパターンはClaude Codeにより良いコンテキストを提供することであることを覚えておいてください - 実際のコード生成（実行ではない）は、これらのコンテキストに基づいてClaudeが行います。