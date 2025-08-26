# SuperClaude 高度ワークフローコレクション

**ステータス**: ✅ **ステータス: 最新** - 洗練されたプロジェクト向けの複雑なコマンドシーケンスとコンテキスト組み合わせ。

**高度使用ガイド**: 複数のコマンド、エージェント、およびClaude Code会話内での慎重なコンテキスト管理を使用する複雑なプロジェクト向けパターン。

## 概要と使用ガイド

**目的**: 慎重なコマンドシーケンシングとコンテキスト管理が必要な複雑な多段階プロジェクト向けの高度SuperClaudeパターン。

**重要**: これらは会話パターンであり、実行ワークフローではありません。すべての作業は提供されたコンテキストに基づいてClaude Code内で発生します。

**主要概念**:
- 会話内でのコマンドシーケンス
- 複数エージェントによるコンテキストレイヤー化
- 段階的洗練アプローチ
- プロジェクトフェーズ管理（手動、自動化なし）

## マルチコンテキストプロジェクトパターン

### フルスタック開発シーケンス

```bash
# 複数コンテキストを使用したeコマースプラットフォーム
# ステップ1: アーキテクチャコンテキスト
@agent-system-architect "eコマースアーキテクチャを設計"

# ステップ2: セキュリティ要件
@agent-security "決済のセキュリティ要件を定義"

# ステップ3: バックエンド実装
/sc:implement "認証と決済処理を含むAPI"
# Claudeは前のステップから蓄積されたコンテキストを使用

# ステップ4: フロントエンド実装
@agent-frontend-architect "レスポンシブUIを設計"
/sc:implement "TypeScriptを使用したReactフロントエンド"

# ステップ5: レビュー
/sc:analyze . --focus quality

# 注意: 各ステップは会話内でコンテキストを構築
# 実際の調整や並列実行は発生しない
```

### 問題解決ワークフロー

```bash
# 複雑なトラブルシューティングアプローチ
# ステップ1: 問題理解
/sc:troubleshoot "アプリケーションパフォーマンス問題"

# ステップ2: エキスパート分析
@agent-performance-engineer "潜在的ボトルネックを分析"
@agent-backend-architect "問題のアーキテクチャをレビュー"

# ステップ3: ソリューション設計
/sc:design "パフォーマンス改善計画"

# ステップ4: 実装
/sc:implement "パフォーマンス最適化"

# コンテキストは蓄積されるが実行はされない
```

## 複雑プロジェクトフェーズ

### プロジェクト初期化パターン

```bash
# 新しいプロジェクトの開始
# 発見フェーズ
/sc:brainstorm "プロジェクトコンセプト"
# Claudeが要件を探索

# 計画フェーズ
/sc:design "システムアーキテクチャ"
@agent-system-architect "レビューと洗練"

# ドキュメント化
/sc:document --type architecture
/sc:save "プロジェクト計画"
# あなたの記録用サマリーを作成（永続ストレージではない）
```

### 段階的開発パターン

```bash
# 機能の段階的構築
# 機能1: 認証
/sc:implement "ユーザー認証"
/sc:test --focus security
/sc:document --type api

# 機能2: ユーザープロファイル（認証コンテキストに基づく）
/sc:implement "ユーザープロファイル管理"
/sc:test --focus functionality

# 機能3: 管理ダッシュボード（前のコンテキストを使用）
/sc:implement "管理ダッシュボード"
@agent-frontend-architect "一貫性を確保"

# 各機能は会話コンテキストに基づいて構築
```

### 移行プロジェクトパターン

```bash
# レガシーシステム移行
# フェーズ1: 分析
/sc:load legacy-system/
/sc:analyze . --focus architecture --verbose
# Claudeが理解を構築

# フェーズ2: 計画
@agent-system-architect "移行戦略を設計"
/sc:workflow "移行計画を作成"

# フェーズ3: 実装
/sc:implement "互換性レイヤー"
/sc:implement "新システムコンポーネント"

# フェーズ4: 検証
/sc:test --focus compatibility
/sc:document --type migration

# 手動フェーズ、自動化ワークフローではない
```

## エンタープライズ規模パターン

### 大規模コードベース分析

```bash
# 大規模プロジェクトの体系的分析
# 概要
/sc:analyze . --overview
# 高レベル理解を取得

# モジュール別集中分析
/sc:analyze auth-module/ --focus security
/sc:analyze api-module/ --focus quality
/sc:analyze frontend/ --focus performance

# 統合
@agent-system-architect "発見を統合"
/sc:workflow "改善推奨事項"

# 注意: 順次分析、並列ではない
```

### マルチテクノロジープロジェクト

```bash
# 多様な技術スタックを持つプロジェクト
# バックエンド（Python）
@agent-python-expert "FastAPIバックエンドを実装"
/sc:implement "async サポート付きPython API"

# フロントエンド（React）
@agent-frontend-architect "Reactフロントエンドを実装"
/sc:implement "TypeScript Reactアプリケーション"

# モバイル（React Native）
/sc:implement "React Nativeモバイルアプリ"

# インフラストラクチャ
@agent-devops-architect "デプロイメントを設計"
/sc:implement "Docker設定"

# 各技術は順次対応
```

## 品質保証ワークフロー

### 包括的レビューパターン

```bash
# マルチ側面コードレビュー
# 品質レビュー
/sc:analyze . --focus quality
@agent-quality-engineer "改善を特定"

# セキュリティレビュー
/sc:analyze . --focus security
@agent-security "脆弱性をチェック"

# アーキテクチャレビュー
@agent-system-architect "設計を評価"

# パフォーマンスレビュー
@agent-performance-engineer "最適化を提案"

# 統合改善
/sc:improve . --fix

# 順次レビュー、並列分析ではない
```

### テスト戦略パターン

```bash
# 包括的テストアプローチ
# テスト計画
/sc:design "テスト戦略"

# ユニットテスト
/sc:test --type unit
# Claudeがユニットテストコードを生成

# 統合テスト
/sc:test --type integration
# Claudeが統合テストコードを生成

# E2Eテスト
/sc:test --type e2e
# ClaudeがE2Eテストシナリオを提案

# ドキュメント化
/sc:document --type testing

# テストコード生成、実行ではない
```

## セッション管理パターン

### 長期プロジェクトセッション

```bash
# 長い会話でのコンテキスト管理
# コンテキストで開始
/sc:load project/

# 段階的作業
/sc:implement "機能A"
/sc:implement "機能B"
# コンテキストが蓄積

# チェックポイント作成
/sc:save "セッションチェックポイント"
# あなたのメモ用サマリーを作成

# 作業継続
/sc:implement "機能C"

# 最終サマリー
/sc:reflect
# 会話進捗をレビュー
```

### コンテキスト更新パターン

```bash
# 会話が長くなりすぎた場合
# 現在の状態を保存
/sc:save "作業完了"
# 次の会話用に出力をコピー

# 新しい会話で:
/sc:load project/
"前の作業: [サマリーを貼り付け]"
# 手動でコンテキストを復元

# 作業続行
/sc:implement "次の機能"
```

## 重要な明確化

### これらのワークフローの実体

- ✅ **会話パターン**: 単一のClaude会話内でのシーケンス
- ✅ **コンテキスト構築**: 理解の段階的蓄積
- ✅ **コマンドシーケンス**: より良い結果のための順序付きコマンド使用
- ✅ **手動フェーズ**: ユーザー制御のプロジェクト進行

### これらのワークフローでないもの

- ❌ **自動化ワークフロー**: 自動実行やオーケストレーションなし
- ❌ **並列処理**: すべてが順次
- ❌ **永続セッション**: 会話間でコンテキスト消失
- ❌ **パフォーマンス最適化**: 最適化するコード実行なし

## ベストプラクティス

### 会話管理

1. **関連作業をまとめる**: 関連タスクを複数会話に分割しない
2. **段階的にコンテキストを構築**: 広く始めてからフォーカス
3. **重要な決定を文書化**: 重要ポイントに`/sc:save`を使用
4. **会話長を管理**: 長すぎる場合は新しい会話を開始

### コマンドシーケンシング

1. **論理的順序**: 分析 → 設計 → 実装 → テスト
2. **コンテキスト蓄積**: 後のコマンドは前のコンテキストから利益
3. **適切な深度**: 分析深度をタスク複雑度に合致
4. **明確なスコープ**: コマンドを特定領域にフォーカス

### エージェント使用

1. **戦略的活性化**: 特定専門知識にエージェントを使用
2. **過負荷回避**: エージェントが多すぎるとフォーカス薄弱
3. **手動制御**: 精密制御に`@agent-`を使用
4. **コンテキストレイヤー化**: 論理的順序でエージェントを追加

## まとめ

SuperClaudeの高度ワークフローは、単一のClaude Codeセッション内で段階的にコンテキストを構築する洗練された会話パターンです。慎重なコマンドシーケンシングとコンテキスト管理を通じてより良い出力を生成するのに役立ちますが、実際のワークフロー実行、並列処理、自動化は含まれません。成功はClaudeの会話スコープ内でコンテキストを効果的にレイヤー化する方法を理解することから来ます。