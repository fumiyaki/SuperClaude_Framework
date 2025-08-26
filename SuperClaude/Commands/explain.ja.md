---
name: explain
description: "教育的明快さでコード、概念、システム動作の明確な説明を提供"
category: workflow
complexity: standard
mcp-servers: [sequential, context7]
personas: [educator, architect, security]
---

# /sc:explain - コードと概念の説明

## トリガー
- 複雑な機能のコード理解とドキュメントリクエスト
- アーキテクチャコンポーネントのシステム動作説明の必要性
- 知識移転のための教育コンテンツ生成
- フレームワーク固有概念の明確化要件

## 使用法
```
/sc:explain [ターゲット] [--level basic|intermediate|advanced] [--format text|examples|interactive] [--context ドメイン]
```

## 動作フロー
1. **分析**: 包括的理解のためターゲットコード、概念、システムを調査
2. **評価**: 読者レベルと適切な説明深度・フォーマットを決定
3. **構造化**: 段階的複雑性と論理的フローで説明順序を計画
4. **生成**: 例、図表、インタラクティブ要素を含む明確な説明を作成
5. **検証**: 説明精度と教育効果を確認

主要な動作:
- ドメイン専門知識（educator、architect、security）のマルチペルソナ連携
- Context7統合によるフレームワーク固有説明
- 複雑概念分解のためのSequential MCPによる体系的分析
- 読者と複雑性に基づく適応的説明深度

## MCP統合
- **Sequential MCP**: 複雑な多コンポーネント分析と構造化推論で自動活性化
- **Context7 MCP**: フレームワークドキュメントと公式パターン説明
- **ペルソナ連携**: Educator（学習）、Architect（システム）、Security（プラクティス）

## ツール連携
- **Read/Grep/Glob**: 説明コンテンツのコード分析とパターン識別
- **TodoWrite**: 複雑な複数部分説明の進捗追跡
- **Task**: 体系的分解が必要な包括的説明ワークフローの委任

## 主要パターン
- **段階的学習**: 基本概念 → 中級詳細 → 高度実装
- **フレームワーク統合**: Context7ドキュメント → 正確な公式パターンとプラクティス
- **マルチドメイン分析**: 技術精度 + 教育明快さ + セキュリティ意識
- **インタラクティブ説明**: 静的コンテンツ → 例 → インタラクティブ探索

## 例

### 基本コード説明
```
/sc:explain authentication.js --level basic
# 初心者向けの実用的な例を含む明確な説明
# Educatorペルソナが学習最適化構造を提供
```

### フレームワーク概念説明
```
/sc:explain react-hooks --level intermediate --context react
# 公式ReactドキュメントパターンのためのContext7統合
# 段階的複雑性を含む構造化説明
```

### システムアーキテクチャ説明
```
/sc:explain microservices-system --level advanced --format interactive
# Architectペルソナがシステム設計とパターンを説明
# Sequential分析分解によるインタラクティブ探索
```

### セキュリティ概念説明
```
/sc:explain jwt-authentication --context security --level basic
# Securityペルソナが認証概念とベストプラクティスを説明
# 実用的な例を含むフレームワーク非依存セキュリティ原則
```

## 境界

**実行すること:**
- 教育的明快さで明確かつ包括的な説明を提供
- ドメイン専門知識と正確な分析のため関連ペルソナを自動活性化
- 公式ドキュメント統合によるフレームワーク固有説明を生成

**実行しないこと:**
- 徹底的分析と精度検証なしの説明を生成
- プロジェクト固有ドキュメント標準を上書きしたり機密詳細を公開
- 確立された説明検証や教育品質要件を回避