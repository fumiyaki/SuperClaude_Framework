---
name: implement
description: "インテリジェントなペルソナ活性化とMCP統合を伴う機能とコードの実装"
category: workflow
complexity: standard
mcp-servers: [context7, sequential, magic, playwright]
personas: [architect, frontend, backend, security, qa-specialist]
---

# /sc:implement - 機能実装

> **コンテキストフレームワークに関する注意**: この動作指示は、Claude Codeユーザーが `/sc:implement` パターンを入力した際に活性化されます。包括的実装のためスペシャリストペルソナとMCPツールの連携をClaude にガイドします。

## トリガー
- コンポーネント、API、完全機能の機能開発リクエスト
- フレームワーク固有要件を持つコード実装の必要性
- 連携した専門知識が必要な多領域開発
- テストと検証統合が必要な実装プロジェクト

## コンテキストトリガーパターン
```
/sc:implement [機能説明] [--type component|api|service|feature] [--framework react|vue|express] [--safe] [--with-tests]
```
**使用法**: Claude Code会話でこれを入力することで、連携した専門知識と体系的開発アプローチによる実装動作モードが活性化されます。

## 動作フロー
1. **分析**: 実装要件を調査し技術コンテキストを検出
2. **計画**: アプローチを選択しドメイン専門知識のため関連ペルソナを活性化
3. **生成**: フレームワーク固有ベストプラクティスで実装コードを作成
4. **検証**: 開発全体を通じてセキュリティと品質検証を適用
5. **統合**: ドキュメントを更新しテスト推奨を提供

主要な動作:
- コンテキストベースペルソナ活性化（architect、frontend、backend、security、qa）
- Context7とMagic MCP統合によるフレームワーク固有実装
- Sequential MCPによる体系的多コンポーネント連携
- 検証のためのPlaywrightとの包括的テスト統合

## MCP統合
- **Context7 MCP**: React、Vue、Angular、Express向けのフレームワークパターンと公式ドキュメント
- **Magic MCP**: UIコンポーネント生成とデザインシステム統合で自動活性化
- **Sequential MCP**: 複雑な多段階分析と実装計画
- **Playwright MCP**: テスト検証と品質保証統合

## ツール連携
- **Write/Edit/MultiEdit**: 実装のためのコード生成と変更
- **Read/Grep/Glob**: 一貫性のためのプロジェクト分析とパターン検出
- **TodoWrite**: 複雑な複数ファイル実装の進捗追跡
- **Task**: 体系的連携が必要な大規模機能開発の委任

## 主要パターン
- **コンテキスト検出**: フレームワーク/技術スタック → 適切なペルソナとMCP活性化
- **実装フロー**: 要件 → コード生成 → 検証 → 統合
- **マルチペルソナ連携**: Frontend + Backend + Security → 包括的ソリューション
- **品質統合**: 実装 → テスト → ドキュメント → 検証

## 例

### Reactコンポーネント実装
```
/sc:implement ユーザープロファイルコンポーネント --type component --framework react
# Magic MCPがデザインシステム統合でUIコンポーネントを生成
# Frontendペルソナがベストプラクティスとアクセシビリティを確保
```

### APIサービス実装
```
/sc:implement ユーザー認証API --type api --safe --with-tests
# Backendペルソナがサーバーサイドロジックとデータ処理を担当
# Securityペルソナが認証ベストプラクティスを確保
```

### フルスタック機能
```
/sc:implement 支払い処理システム --type feature --with-tests
# マルチペルソナ連携：architect、frontend、backend、security
# Sequential MCPが複雑な実装ステップを分解
```

### フレームワーク固有実装
```
/sc:implement ダッシュボードウィジェット --framework vue
# Context7 MCPがVue固有パターンとドキュメントを提供
# 公式ベストプラクティスでフレームワーク適切な実装
```

## 境界

**実行すること:**
- インテリジェントなペルソナ活性化とMCP連携で機能を実装
- フレームワーク固有ベストプラクティスとセキュリティ検証を適用
- テストとドキュメント統合を伴う包括的実装を提供

**実行しないこと:**
- 適切なペルソナ相談なしのアーキテクチャ決定
- セキュリティポリシーやアーキテクチャ制約と競合する機能の実装
- ユーザー指定の安全制約を上書きしたり品質ゲートを回避