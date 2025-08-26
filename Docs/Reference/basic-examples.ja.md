# SuperClaude 基本サンプルコレクション

**ステータス**: ✅ **ステータス: 最新** - 必須コマンド、シングルエージェントワークフロー、一般的な開発タスク。

**クイックリファレンスガイド**: 初心者向けのコピペ対応サンプル、基本的なSuperClaude使用パターンと基礎的な開発ワークフローにフォーカス。

> **📝 コンテキスト注記**: これらのサンプルは、Claude Codeが特定のコンテキストファイルを読み込み、そこで定義された行動を採用するよう起動させる`/sc:`コマンドと`@agent-`呼び出しを示しています。洗練度は実行可能なソフトウェアからではなく、行動指示から来ています。

## 概要と使用ガイド

**目的**: 日常の開発タスクのための必須SuperClaudeコマンドとパターン。初めてのSuperClaude体験はここから始めましょう。

**対象読者**: 新規ユーザー、SuperClaude基礎を学ぶ開発者、即座のタスク適用

**使用パターン**: コピー → 適応 → 実行 → 結果から学習

**主要機能**:
- コアSuperClaude機能を実証するサンプル
- 即座の応用のための明確なパターン
- 明確な学習のためのシングルフォーカスサンプル
- 基本スコープ内での段階的複雑性

## 必須ワンライナーコマンド

### コア開発コマンド

#### コマンド: /sc:brainstorm
**目的**: インタラクティブなプロジェクト発見と要件収集
**構文**: `/sc:brainstorm "プロジェクト説明"`
**例**:
```bash
/sc:brainstorm "フィットネス追跡のためのモバイルアプリ"
# 期待される結果: ソクラテス式対話、要件引き出し、実現可能性分析
```
**動作**: インタラクティブ発見対話と要件分析を起動

#### コマンド: /sc:analyze
**目的**: 既存コードベースの問題と改善を分析
**構文**: `/sc:analyze [対象] --focus [ドメイン]`
**例**:
```bash
/sc:analyze src/ --focus security
# 期待される結果: 包括的セキュリティ監査、脆弱性レポート、改善提案
```
**動作**: 包括的セキュリティ分析と改善推奨を提供

#### コマンド: /sc:implement
**目的**: ベストプラクティスで完全な機能を実装
**構文**: `/sc:implement "要件付き機能説明"`
**例**:
```bash
/sc:implement "JWTとレート制限付きユーザー認証"
# 期待される結果: 完全な認証実装、セキュリティ検証、テスト含む
```
**動作**: セキュリティと品質基準に従った完全実装を提供

#### コマンド: /sc:troubleshoot
**目的**: 問題を体系的にトラブルシューティングして修正
**構文**: `/sc:troubleshoot "問題説明"`
**例**:
```bash
/sc:troubleshoot "ユーザーログインでAPIが500エラーを返す"
# 期待される結果: ステップバイステップ診断、根本原因特定、解決策ランキング
```
**検証**: 根本原因分析 + Sequential推論 + 体系的デバッグを活性化

#### コマンド: /sc:test
**目的**: 既存コードの包括的テストを生成
**構文**: `/sc:test [対象] --focus [ドメイン]`
**例**:
```bash
/sc:test --focus quality
# 期待される結果: テストスイート、品質メトリクス、カバレッジレポート
```
**検証**: 品質エンジニア + テスト自動化を活性化

### クイック分析コマンド

#### コマンド: /sc:analyze（品質フォーカス）
**目的**: プロジェクト構造と品質概要
**構文**: `/sc:analyze [対象] --focus quality`
**例**:
```bash
/sc:analyze . --focus quality
```

#### コマンド: /sc:analyze（セキュリティフォーカス）
**目的**: セキュリティ重視のコードレビュー
**構文**: `/sc:analyze [対象] --focus security [--think]`
**例**:
```bash
/sc:analyze src/ --focus security --think
```

#### コマンド: /sc:analyze（パフォーマンスフォーカス）
**目的**: パフォーマンスボトルネック特定
**構文**: `/sc:analyze [対象] --focus performance`
**例**:
```bash
/sc:analyze api/ --focus performance
```

#### コマンド: /sc:analyze（アーキテクチャフォーカス）
**目的**: リファクタリングのためのアーキテクチャ評価
**構文**: `/sc:analyze [対象] --focus architecture [--serena]`
**例**:
```bash
/sc:analyze . --focus architecture --serena
```

## 手動エージェント呼び出しサンプル

### 直接専門家活性化

#### パターン: @agent-[専門家]
**目的**: 自動活性化の代わりに特定ドメイン専門家を手動呼び出し
**構文**: `@agent-[専門家] "タスクまたは質問"`

#### Pythonエキスパート
```bash
@agent-python-expert "このデータ処理パイプラインをパフォーマンス最適化"
# 期待される結果: Python特有の最適化、非同期パターン、メモリ管理
```

#### セキュリティエンジニア
```bash
@agent-security "この認証システムの脆弱性をレビュー"
# 期待される結果: OWASP準拠チェック、脆弱性評価、セキュアコーディング推奨
```

#### フロントエンドアーキテクト
```bash
@agent-frontend-architect "レスポンシブコンポーネントアーキテクチャを設計"
# 期待される結果: コンポーネントパターン、状態管理、アクセシビリティ考慮
```

#### 品質エンジニア
```bash
@agent-quality-engineer "決済モジュールの包括的テストカバレッジを作成"
# 期待される結果: テスト戦略、ユニット/統合/E2Eテスト、エッジケース
```

### 自動と手動パターンの組み合わせ

#### パターン: コマンド + 手動オーバーライド
```bash
# ステップ1: 自動活性化でコマンドを使用
/sc:implement "ユーザープロファイル管理システム"
# 自動活性化: backend-architect、おそらくfrontend

# ステップ2: 特定エキスパートレビューを追加
@agent-security "データプライバシー準拠のためのプロファイルシステムをレビュー"
# 的を絞ったレビューのための手動活性化

# ステップ3: パフォーマンス最適化
@agent-performance-engineer "プロファイル取得のデータベースクエリを最適化"
# 特定最適化のための手動活性化
```

#### パターン: 順次専門家チェーン
```bash
# 設計フェーズ
@agent-system-architect "eコマースのマイクロサービスアーキテクチャを設計"

# セキュリティレビュー
@agent-security "セキュリティ境界のアーキテクチャをレビュー"

# 実装ガイダンス
@agent-backend-architect "サービス通信パターンを実装"

# DevOps設定
@agent-devops-architect "マイクロサービスのCI/CDを設定"
```

## 基本使用パターン

### 発見 → 実装パターン
```bash
# ステップ1: 要件を探索し理解
/sc:brainstorm "プロジェクト管理のWebダッシュボード"
# 期待される結果: 要件発見、機能優先順位付け、技術範囲

# ステップ2: 技術アプローチを分析
/sc:analyze "ダッシュボードアーキテクチャパターン" --focus architecture --c7
# 期待される結果: アーキテクチャパターン、技術推奨、実装戦略

# ステップ3: コア機能を実装
/sc:implement "タスク管理とチームコラボレーション付きReactダッシュボード"
# 期待される結果: モダンReactパターンでの完全ダッシュボード実装
```

### 開発 → 品質パターン
```bash
# ステップ1: 機能を構築
/sc:implement "メール確認付きユーザー登録"
# 期待される結果: メール統合付き登録システム

# ステップ2: 徹底テスト
/sc:test --focus quality
# 期待される結果: 包括的テストカバレッジと検証

# ステップ3: レビューと改善
/sc:analyze . --focus quality && /sc:implement "品質改善"
# 期待される結果: 品質評価と的を絞った改善
```

### 問題 → 解決パターン
```bash
# ステップ1: 問題を理解
/sc:troubleshoot "ユーザーダッシュボードでのデータベースクエリが遅い"
# 期待される結果: 体系的問題診断と根本原因分析

# ステップ2: 影響されるコンポーネントを分析
/sc:analyze db/ --focus performance
# 期待される結果: データベースパフォーマンス分析と最適化機会

# ステップ3: 解決策を実装
/sc:implement "データベースクエリ最適化とキャッシュ"
# 期待される結果: 測定可能な影響を持つパフォーマンス改善
```

## はじめてのサンプル

### 初回プロジェクト分析
```bash
# 完全プロジェクト理解ワークフロー
/sc:load . && /sc:analyze --focus quality

# 期待される結果:
# - プロジェクト構造分析とドキュメント
# - 全ファイルにわたるコード品質評価
# - コンポーネント関係を含むアーキテクチャ概要
# - セキュリティ監査とパフォーマンス推奨

# 活性化: Serena（プロジェクト読み込み） + analyzer + security-engineer + performance-engineer
# 出力: 実用的洞察を含む包括的プロジェクトレポート

# 異なるフォーカスのバリエーション:
/sc:analyze src/ --focus quality          # コード品質のみ
/sc:analyze . --scope file               # クイックファイル分析
/sc:analyze backend/ --focus security    # バックエンドセキュリティレビュー
```

### インタラクティブ要件発見
```bash
# 曖昧なアイデアを具体的要件に変換
/sc:brainstorm "リモートチーム向け生産性アプリ"

# 期待されるインタラクション:
# - ユーザーニーズと課題についてのソクラテス式質問
# - 機能優先順位付けと範囲定義
# - 技術的実現可能性評価
# - 構造化要件ドキュメント生成

# 活性化: Brainstormingモード + system-architect + requirements-analyst
# 出力: 明確な仕様を持つプロダクト要求ドキュメント（PRD）

# 進展のためのフォローアップコマンド:
/sc:analyze "チームコラボレーションアーキテクチャ" --focus architecture --c7
/sc:implement "ReactとWebSocketを使用したリアルタイムメッセージングシステム"
```

### シンプル機能実装
```bash
# 完全認証システム
/sc:implement "JWTトークンとパスワードハッシュ付きユーザーログイン"

# 期待される実装:
# - bcryptでのセキュアパスワードハッシュ
# - JWTトークン生成と検証
# - 適切なエラーハンドリング付きログイン/ログアウトエンドポイント
# - 検証付きフロントエンドログインフォーム

# 活性化: security-engineer + backend-architect + Context7
# 出力: 本番対応認証システム

# 異なる認証ニーズのバリエーション:
/sc:implement "GoogleとGitHubのOAuth統合"
/sc:implement "メール確認付きパスワードリセットフロー"
/sc:implement "TOTPを使用した二要素認証"
```

## 一般的な開発タスク

### API開発基本
```bash
# CRUD操作付きREST API
/sc:implement "ブログ投稿の検証付きExpress.js REST API"
# 期待される結果: 適切なHTTPメソッド、検証、エラーハンドリング付き完全REST API

# APIドキュメント生成
/sc:analyze api/ --focus architecture --c7
# 期待される結果: 使用例付き包括的APIドキュメント

# APIテスト設定
/sc:test --focus api --type integration
# 期待される結果: APIエンドポイントの統合テストスイート
```

### フロントエンドコンポーネント開発
```bash
# モダンパターンのReactコンポーネント
/sc:implement "フォーム検証と画像アップロード付きReactユーザープロファイルコンポーネント"
# 活性化: frontend-architect + Magic MCP + アクセシビリティパターン
# 期待される結果: フック、検証、アクセシビリティ付きモダンReactコンポーネント

# コンポーネントテスト
/sc:test src/components/ --focus quality
# 期待される結果: React Testing Libraryでのコンポーネントテスト

# レスポンシブデザイン実装
/sc:implement "モバイルメニュー付きレスポンシブナビゲーションコンポーネント"
# 期待される結果: アクセシビリティ付きモバイルファーストレスポンシブナビゲーション
```

### データベース統合
```bash
# ORMでのデータベース設定
/sc:implement "Prisma ORMとマイグレーション付きPostgreSQL統合"
# 期待される結果: データベーススキーマ、ORM設定、マイグレーションシステム

# データベースクエリ最適化
/sc:analyze db/ --focus performance
# 期待される結果: クエリパフォーマンス分析と最適化提案

# データ検証とセキュリティ
/sc:implement "入力検証とSQLインジェクション防止"
# 期待される結果: 包括的入力検証とセキュリティ対策
```

## 基本トラブルシューティングサンプル

### 一般的なAPI問題
```bash
# パフォーマンス問題
/sc:troubleshoot "API応答時間が200msから2秒に増加"
# 活性化: root-cause-analyst + performance-engineer + Sequential推論
# 期待される結果: 体系的診断、根本原因特定、解決策ランキング

# 認証エラー
/sc:troubleshoot "有効ユーザーでJWTトークン検証が失敗"
# 期待される結果: トークン検証分析、セキュリティ評価、修正実装

# データベース接続問題
/sc:troubleshoot "負荷時にデータベース接続プール枯渇"
# 期待される結果: 接続分析、設定修正、スケーリング推奨
```

### フロントエンドデバッグ
```bash
# Reactレンダリング問題
/sc:troubleshoot "データ変更時にReactコンポーネントが更新されない"
# 期待される結果: 状態管理分析、再レンダリング最適化、デバッグガイド

# パフォーマンス問題
/sc:troubleshoot "大きなコンポーネントツリーでReactアプリの読み込みが遅い"
# 期待される結果: パフォーマンス分析、最適化戦略、コード分割推奨

# ビルド失敗
/sc:troubleshoot "依存関係競合でwebpackビルドが失敗"
# 期待される結果: 依存関係分析、競合解決、ビルド最適化
```

### 開発環境問題
```bash
# セットアップ問題
/sc:troubleshoot "npm install後にNode.jsアプリケーションが起動しない"
# 期待される結果: 環境分析、依存関係トラブルシューティング、設定修正

# テスト失敗
/sc:troubleshoot "ローカルでは成功するがCIで失敗するテスト"
# 期待される結果: 環境比較、CI設定分析、修正推奨

# デプロイメント問題
/sc:troubleshoot "本番デプロイメントでアプリケーションがクラッシュ"
# 期待される結果: 本番環境分析、設定検証、デプロイメント修正
```

## コピペクイック解決策

### 即座のプロジェクト設定
```bash
# TypeScript付きの新しいReactプロジェクト
/sc:implement "ルーティング、状態管理、テスト設定付きReact TypeScriptプロジェクト"
@agent-frontend-architect "プロジェクト構造をレビューし最適化"

# 新しいNode.js APIサーバー
/sc:implement "JWT認証とPostgreSQL統合付きExpress.js REST API"
@agent-backend-architect "スケーラビリティとベストプラクティスを確保"

# Python Web API
/sc:implement "非同期PostgreSQLと認証ミドルウェア付きFastAPIアプリケーション"
@agent-python-expert "非同期パターンと依存関係注入を最適化"

# Next.jsフルスタックアプリ
/sc:implement "App Router、TypeScript、Tailwind CSS付きNext.js 14アプリケーション"
@agent-system-architect "最適なデータフェッチ戦略を設計"
```

### クイック品質改善
```bash
# コード品質向上
/sc:analyze . --focus quality && /sc:implement "コード品質改善"
@agent-quality-engineer "品質メトリクスダッシュボードを作成"

# セキュリティ強化
/sc:analyze . --focus security && /sc:implement "セキュリティ改善"

# テストカバレッジ改善
/sc:test --focus quality && /sc:implement "追加テストカバレッジ"
```

### 一般的な機能実装
```bash
# ユーザー認証システム
/sc:implement "登録、ログイン、パスワードリセット付き完全ユーザー認証"

# ファイルアップロード機能
/sc:implement "画像リサイズとクラウドストレージ付きセキュアファイルアップロード"

# リアルタイム機能
/sc:implement "WebSocketとメッセージ永続化付きリアルタイムチャット"

# 決済処理
/sc:implement "サブスクリプション管理付きStripe決済統合"

# メール機能
/sc:implement "テンプレートと配信追跡付きメールサービス"
```

## 基本フラグサンプル

### 分析深度制御
```bash
# クイック分析
/sc:analyze src/ --scope file

# 標準分析
/sc:analyze . --think

# 深い分析
/sc:analyze . --think-hard --focus architecture
```

### フォーカス領域選択
```bash
# セキュリティ重視分析
/sc:analyze . --focus security

# 特定フォーカス付き実装
/sc:implement "API最適化" --focus architecture

# 品質重視テスト
/sc:test --focus quality
```

### ツール統合
```bash
# 公式パターンにContext7を使用
/sc:implement "Reactフック実装" --c7

# プロジェクトメモリにSerenaを使用
/sc:analyze . --serena --focus architecture

# 効率的トークン使用
/sc:analyze large-project/ --uc
```

## 学習進歩ワークフロー

### 第1週: 基礎
```bash
# 1-2日目: 基本コマンド
/sc:analyze . --focus quality
/sc:implement "シンプル機能"
/sc:test --focus quality

# 3-4日目: トラブルシューティング
/sc:troubleshoot "特定の問題"
/sc:analyze problem-area/ --focus relevant-domain

# 5-7日目: 統合
/sc:brainstorm "プロジェクトアイデア"
/sc:implement "コア機能"
/sc:test --focus quality
```

### 第2週: パターン
```bash
# ワークフローパターン
/sc:brainstorm → /sc:analyze → /sc:implement → /sc:test

# 問題解決パターン
/sc:troubleshoot → /sc:analyze → /sc:implement

# 品質パターン
/sc:analyze → /sc:implement → /sc:test → /sc:analyze
```

### 第3-4週: 統合
```bash
# マルチステッププロジェクト
/sc:brainstorm "より大きなプロジェクト"
/sc:implement "フェーズ1"
/sc:test --focus quality
/sc:implement "フェーズ2"
/sc:test --focus integration
```

## 次のステップ

### 中級の準備はできましたか？
- すべての基本コマンドに習熟
- シンプルワークフローを独立して完了可能
- エージェント活性化とツール選択の理解
- マルチステッププロジェクトの準備完了

### 学習継続:
- **高度ワークフロー**: 複雑なオーケストレーションとマルチエージェント協調
- **統合パターン**: フレームワーク統合とクロスツール協調
- **ベストプラクティスガイド**: 最適化戦略とエキスパートテクニック

### 成功指標:
- 一般的な開発問題を独立して解決可能
- 異なるフラグとフォーカスをいつ使用するかを理解
- サンプルを特定プロジェクトニーズに適応可能
- より複雑なSuperClaude機能を探索する準備完了

---

**覚えておくこと**: シンプルに始め、頻繁に練習し、段階的に複雑性を増します。これらの基本サンプルは、すべての高度なSuperClaude使用の基盤を形成します。