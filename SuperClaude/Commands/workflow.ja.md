---
name: workflow
description: "PRDと機能要件から構造化実装ワークフローを生成"
category: orchestration
complexity: advanced
mcp-servers: [sequential, context7, magic, playwright, morphllm, serena]
personas: [architect, analyzer, frontend, backend, security, devops, project-manager]
---

# /sc:workflow - 実装ワークフロージェネレーター

## トリガー
- 実装計画のためのPRDと機能仕様分析
- 開発プロジェクトの構造化ワークフロー生成
- 複雑実装戦略のためのマルチペルソナ連携
- セッション間ワークフロー管理と依存関係マッピング

## 使用法
```
/sc:workflow [PRDファイル|機能説明] [--strategy systematic|agile|enterprise] [--depth shallow|normal|deep] [--parallel]
```

## 動作フロー
1. **分析**: PRDと機能仕様を解析し実装要件を理解
2. **計画**: 依存関係マッピングとタスクオーケストレーションを伴う包括的ワークフロー構造を生成
3. **連携**: ドメイン専門知識と実装戦略のため複数ペルソナを活性化
4. **実行**: 自動タスク連携を伴う構造化ステップバイステップワークフローを作成
5. **検証**: 品質ゲートを適用し領域間でワークフロー完全性を確認

主要な動作:
- アーキテクチャ、フロントエンド、バックエンド、セキュリティ、DevOps領域でのマルチペルソナオーケストレーション
- 専門ワークフロー分析のためのインテリジェントルーティングを伴う高度MCP連携
- プログレッシブワークフロー強化と並行処理を伴う体系的実行
- 包括的依存関係追跡を伴うセッション間ワークフロー管理

## MCP統合
- **Sequential MCP**: 複雑な多段階ワークフロー分析と体系的実装計画
- **Context7 MCP**: フレームワーク固有ワークフローパターンと実装ベストプラクティス
- **Magic MCP**: UI/UXワークフロー生成とデザインシステム統合戦略
- **Playwright MCP**: テストワークフロー統合と品質保証自動化
- **Morphllm MCP**: 大規模ワークフロー変換とパターンベース最適化
- **Serena MCP**: セッション間ワークフロー永続化、メモリ管理、プロジェクトコンテキスト

## ツール連携
- **Read/Write/Edit**: PRD分析とワークフロードキュメント生成
- **TodoWrite**: 複雑な多段階ワークフロー実行の進捗追跡
- **Task**: 並行ワークフロー生成とマルチエージェント連携の高度委任
- **WebSearch**: 技術調査、フレームワーク検証、実装戦略分析
- **sequentialthinking**: 複雑ワークフロー依存関係分析のための構造化推論

## 主要パターン
- **PRD分析**: ドキュメント解析 → 要件抽出 → 実装戦略開発
- **ワークフロー生成**: タスク分解 → 依存関係マッピング → 構造化実装計画
- **多領域連携**: 機能横断的専門知識 → 包括的実装戦略
- **品質統合**: ワークフロー検証 → テスト戦略 → デプロイ計画

## 例

### 体系的PRDワークフロー
```
/sc:workflow ClaudeDocs/PRD/feature-spec.md --strategy systematic --depth deep
# 体系的ワークフロー生成を伴う包括的PRD分析
# 完全実装戦略のためのマルチペルソナ連携
```

### アジャイル機能ワークフロー
```
/sc:workflow "ユーザー認証システム" --strategy agile --parallel
# 並行タスク連携を伴うアジャイルワークフロー生成
# フレームワークとUIワークフローパターンのためのContext7とMagic MCP
```

### エンタープライズ実装計画
```
/sc:workflow enterprise-prd.md --strategy enterprise --validate
# 包括的検証を伴うエンタープライズ規模ワークフロー
# コンプライアンスと拡張性のためのsecurity、devops、architectペルソナ
```

### セッション間ワークフロー管理
```
/sc:workflow project-brief.md --depth normal
# Serena MCPがセッション間ワークフローコンテキストと永続化を管理
# メモリ駆動インサイトによるプログレッシブワークフロー強化
```

## 境界

**実行すること:**
- PRDと機能仕様から包括的実装ワークフローを生成
- 完全実装戦略のため複数ペルソナとMCPサーバーを連携
- セッション間ワークフロー管理とプログレッシブ強化機能を提供

**実行しないこと:**
- ワークフロー計画と戦略を超えた実際の実装タスクを実行
- 適切な分析と検証なしで確立された開発プロセスを上書き
- 包括的要件分析と依存関係マッピングなしでワークフローを生成