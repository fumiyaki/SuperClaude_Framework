# SuperClaude 高度パターン

**高度コンテキスト使用パターン**: 複雑なプロジェクトに取り組む経験豊富なSuperClaudeユーザー向けのコマンド、エージェント、フラグの洗練された組み合わせ。

**覚えておくこと**: SuperClaudeはClaude Codeにコンテキストを提供します。ここでのパターンはすべて、コードの実行やプロセスの調整ではなく、コンテキストを通じてClaudeの行動を導くことについてです。

## 目次

### コンテキスト組み合わせパターン
- [マルチエージェントコンテキストパターン](#マルチエージェントコンテキストパターン) - 複数の専門コンテキストの組み合わせ
- [コマンドシーケンシングパターン](#コマンドシーケンシングパターン) - 効果的なコマンド組み合わせ
- [フラグ組み合わせ戦略](#フラグ組み合わせ戦略) - 高度なフラグ使用法

### ワークフローパターン
- [複雑プロジェクトパターン](#複雑プロジェクトパターン) - 大規模プロジェクトアプローチ
- [移行パターン](#移行パターン) - レガシーシステムの現代化
- [レビューと監査パターン](#レビューと監査パターン) - 包括的分析

## マルチエージェントコンテキストパターン

### 専門コンテキストの組み合わせ

**セキュリティ + バックエンドパターン:**
```bash
# セキュリティ重視のバックエンド開発
@agent-security "認証要件を定義"
@agent-backend-architect "セキュリティ要件を含むAPI設計"
/sc:implement "セキュアなAPIエンドポイント"

# 何が起こるか:
# 1. セキュリティコンテキストが最初に読み込まれる
# 2. バックエンドコンテキストが追加される
# 3. 両方のコンテキストによって実装が導かれる
# 注意: コンテキストは実行ではなくClaudeの理解において組み合わされる
```

**フロントエンド + UX + アクセシビリティパターン:**
```bash
# 包括的フロントエンド開発
@agent-frontend-architect "コンポーネントアーキテクチャを設計"
/sc:implement "アクセシブルなReactコンポーネント" --magic
@agent-quality-engineer "アクセシビリティ準拠をレビュー"

# コンテキストのレイヤー化:
# - フロントエンドパターンが構造を導く
# - Magic MCPがUIコンポーネントを提供（設定されている場合）
# - 品質コンテキストが基準を確保
```

### 手動 vs 自動エージェント選択

**明示制御パターン:**
```bash
# どのコンテキストを読み込むかを手動制御
@agent-python-expert "データパイプラインを実装"
# Pythonコンテキストのみ、自動活性化なし

# vs 自動選択
/sc:implement "Pythonデータパイプライン"
# キーワードに基づいて複数エージェントを活性化する可能性
```

**自動選択の上書き:**
```bash
# 不要なエージェント活性化を防ぐ
/sc:implement "シンプルなユーティリティ" --no-mcp
@agent-backend-architect "シンプルに保つ"
# コンテキストを指定されたエージェントのみに制限
```

## コマンドシーケンシングパターン

### 段階的洗練パターン

```bash
# 広く始めて、次にフォーカス
/sc:analyze project/
# 一般的分析

/sc:analyze project/core/ --focus architecture
# 構造にフォーカス

/sc:analyze project/core/auth/ --focus security --think-hard
# セキュリティの深い分析

# 各コマンドは会話内で前のコンテキストに基づいて構築される
```

### 発見から実装パターン

```bash
# 完全な機能開発フロー
/sc:brainstorm "機能アイデア"
# 要件を探索

/sc:design "機能アーキテクチャ"
# 構造を作成

@agent-backend-architect "設計をレビュー"
# エキスパートレビュー

/sc:implement "設計に基づく機能"
# 実装は設計に従う

/sc:test --validate
# 検証アプローチ
```

### 反復改善パターン

```bash
# 複数の改善パス
/sc:analyze code/ --focus quality
# 問題を特定

/sc:improve code/ --fix
# 最初の改善パス

@agent-refactoring-expert "さらなる改善を提案"
# エキスパート提案

/sc:improve code/ --fix --focus maintainability
# 洗練された改善
```

## フラグ組み合わせ戦略

### 分析深度制御

```bash
# クイックオーバービュー
/sc:analyze . --overview --uc
# 高速、圧縮出力

# 標準分析
/sc:analyze . --think
# 構造化思考

# 深い分析
/sc:analyze . --think-hard --verbose
# 包括的分析

# 最大深度（控えめに使用）
/sc:analyze . --ultrathink
# 徹底分析
```

### MCPサーバー選択

```bash
# 選択的MCP使用
/sc:implement "Reactコンポーネント" --magic --c7
# MagicとContext7 MCPのみ

# 全MCPを無効化
/sc:implement "シンプル関数" --no-mcp
# 純粋Claudeコンテキストのみ

# 利用可能な全MCP
/sc:analyze complex-system/ --all-mcp
# 最大ツール可用性（設定されている場合）
```

## 複雑プロジェクトパターン

### 大規模コードベース分析

```bash
# 大規模プロジェクトの体系的探索
# ステップ1: 構造理解
/sc:load project/
/sc:analyze . --overview --focus architecture

# ステップ2: 問題領域を特定
@agent-quality-engineer "高リスクモジュールを特定"

# ステップ3: 特定領域への深掘り
/sc:analyze high-risk-module/ --think-hard --focus quality

# ステップ4: 実装計画
/sc:workflow "分析に基づく改善計画"
```

### マルチモジュール開発

```bash
# 相互接続モジュールの開発
# フロントエンドモジュール
/sc:implement "ユーザーインターフェースモジュール"
@agent-frontend-architect "一貫性を確保"

# バックエンドモジュール
/sc:implement "APIモジュール"
@agent-backend-architect "互換性を確保"

# 統合レイヤー
/sc:implement "フロントエンド-バックエンド統合"
# 両方の前の実装からのコンテキストがこれを導く
```

### クロステクノロジープロジェクト

```bash
# 複数技術を持つプロジェクト
# Pythonバックエンド
@agent-python-expert "FastAPIバックエンドを実装"

# Reactフロントエンド
@agent-frontend-architect "Reactフロントエンドを実装"

# DevOps設定
@agent-devops-architect "デプロイメント設定を作成"

# 統合ドキュメント
/sc:document --type integration
```

## 移行パターン

### レガシーシステム分析

```bash
# レガシーシステムの理解
/sc:load legacy-system/
/sc:analyze . --focus architecture --verbose

@agent-refactoring-expert "現代化機会を特定"
@agent-system-architect "移行戦略を提案"

/sc:workflow "移行計画を作成"
```

### 段階的移行

```bash
# ステップバイステップ移行アプローチ
# フェーズ1: 分析
/sc:analyze legacy-module/ --comprehensive

# フェーズ2: 新アーキテクチャ設計
@agent-system-architect "モダンな代替を設計"

# フェーズ3: 実装
/sc:implement "互換性レイヤー付きモダンモジュール"

# フェーズ4: 検証
/sc:test --focus compatibility
```

## レビューと監査パターン

### セキュリティ監査パターン

```bash
# 包括的セキュリティレビュー
/sc:analyze . --focus security --think-hard
@agent-security "認証と認可をレビュー"
@agent-security "OWASP脆弱性をチェック"
/sc:document --type security-audit
```

### コード品質レビュー

```bash
# マルチ側面品質レビュー
/sc:analyze src/ --focus quality
@agent-quality-engineer "テストカバレッジをレビュー"
@agent-refactoring-expert "コード臭を特定"
/sc:improve --fix --preview
```

### アーキテクチャレビュー

```bash
# システムアーキテクチャ評価
@agent-system-architect "現在のアーキテクチャをレビュー"
/sc:analyze . --focus architecture --think-hard
@agent-performance-engineer "ボトルネックを特定"
/sc:design "最適化推奨事項"
```

## 重要な明確化

### これらのパターンが実際に行うこと

- ✅ **Claudeの思考を導く**: 構造化アプローチを提供
- ✅ **コンテキストを組み合わせる**: 複数の専門領域をレイヤー化
- ✅ **出力品質を改善**: より良いコンテキストによるより良いコード生成
- ✅ **ワークフローを構造化**: 複雑なタスクを整理

### これらのパターンが行わないこと

- ❌ **並列実行**: すべてが順次コンテキスト読み込み
- ❌ **プロセス調整**: 実際のプロセス調整なし
- ❌ **パフォーマンス最適化**: コードが実行されないため、パフォーマンス影響なし
- ❌ **セッション間の永続化**: 各会話は独立

## 高度使用のベストプラクティス

### コンテキスト管理

1. **意図的にレイヤー化**: 論理的順序でコンテキストを追加
2. **過負荷を避ける**: エージェントが多すぎるとフォーカスが薄まる
3. **手動制御を使用**: 必要時に自動活性化を上書き
4. **会話フローを維持**: 関連作業を同じ会話内で保持

### コマンド効率

1. **論理的に進歩**: 広い → 特定 → 実装
2. **コンテキストを再利用**: 後のコマンドは前のコンテキストから利益を得る
3. **決定を文書化**: 重要なサマリーに`/sc:save`を使用
4. **適切にスコープ**: 管理可能なチャンクにフォーカス

### フラグ使用

1. **タスク複雑性に合致**: シンプルなタスクに`--ultrathink`は不要
2. **出力制御**: 簡潔な結果に`--uc`を使用
3. **MCPを管理**: 必要なサーバーのみを活性化
4. **競合回避**: 矛盾するフラグを使用しない

## まとめ

SuperClaudeの高度パターンは、洗練されたコンテキスト管理とコマンドシーケンシングについてです。より豊かで構造化されたコンテキストを提供することで、Claude Codeがより良い出力を生成するのを助けます。覚えておくこと: すべての「調整」と「最適化」は、実際の実行や並列処理ではなく、Claudeがコンテキストを解釈する方法で発生します。