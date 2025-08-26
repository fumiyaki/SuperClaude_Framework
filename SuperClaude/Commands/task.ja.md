---
name: task
description: "インテリジェントワークフロー管理と委任による複雑タスクの実行"
category: special
complexity: advanced
mcp-servers: [sequential, context7, magic, playwright, morphllm, serena]
personas: [architect, analyzer, frontend, backend, security, devops, project-manager]
---

# /sc:task - 拡張タスク管理

## トリガー
- マルチエージェント連携と委任が必要な複雑タスク
- 構造化ワークフロー管理とセッション間永続化が必要なプロジェクト
- インテリジェントMCPサーバールーティングとドメイン専門知識が必要な操作
- 体系的実行とプログレッシブ強化が有益なタスク

## 使用法
```
/sc:task [アクション] [ターゲット] [--strategy systematic|agile|enterprise] [--parallel] [--delegate]
```

## 動作フロー
1. **分析**: タスク要件を解析し最適実行戦略を決定
2. **委任**: 適切なMCPサーバーにルーティングし関連ペルソナを活性化
3. **連携**: インテリジェントワークフロー管理と並行処理でタスクを実行
4. **検証**: 品質ゲートと包括的タスク完了確認を適用
5. **最適化**: パフォーマンスを分析し強化推奨を提供

主要な動作:
- architect、frontend、backend、security、devops領域でのマルチペルソナ連携
- インテリジェントMCPサーバールーティング（Sequential、Context7、Magic、Playwright、Morphllm、Serena）
- プログレッシブタスク強化とセッション間永続化を伴う体系的実行
- 階層分解と依存関係管理を伴う高度タスク委任

## MCP統合
- **Sequential MCP**: 複雑な多段階タスク分析と体系的実行計画
- **Context7 MCP**: フレームワーク固有パターンと実装ベストプラクティス
- **Magic MCP**: UI/UXタスク連携とデザインシステム統合
- **Playwright MCP**: テストワークフロー統合と検証自動化
- **Morphllm MCP**: 大規模タスク変換とパターンベース最適化
- **Serena MCP**: セッション間タスク永続化とプロジェクトメモリ管理

## ツール連携
- **TodoWrite**: Epic → Story → Taskレベルでの階層タスク分解と進捗追跡
- **Task**: 複雑なマルチエージェント連携とサブタスク管理の高度委任
- **Read/Write/Edit**: タスクドキュメントと実装連携
- **sequentialthinking**: 複雑タスク依存関係分析のための構造化推論

## 主要パターン
- **タスク階層**: Epicレベル目標 → Story連携 → Task実行 → Subtaskの粒度
- **戦略選択**: Systematic（包括的） → Agile（反復的） → Enterprise（ガバナンス）
- **マルチエージェント連携**: ペルソナ活性化 → MCPルーティング → 並行実行 → 結果統合
- **セッション間管理**: タスク永続化 → コンテキスト継続性 → プログレッシブ強化

## 例

### 複雑機能開発
```
/sc:task create "エンタープライズ認証システム" --strategy systematic --parallel
# 多領域連携による包括的タスク分解
# architect、security、backend、frontendペルソナを活性化
```

### アジャイルスプリント連携
```
/sc:task execute "機能バックログ" --strategy agile --delegate
# インテリジェント委任による反復タスク実行
# スプリント継続性のためのセッション間永続化
```

### 多領域統合
```
/sc:task execute "マイクロサービスプラットフォーム" --strategy enterprise --parallel
# コンプライアンス検証を伴うエンタープライズ規模連携
# 複数技術領域での並行実行
```

## 境界

**実行すること:**
- マルチエージェント連携とインテリジェント委任による複雑タスクを実行
- セッション間永続化を伴う階層タスク分解を提供
- 最適タスク成果のため複数MCPサーバーとペルソナを連携

**実行しないこと:**
- 高度オーケストレーションが不要な単純タスクを実行
- 速度や利便性のため品質標準を妥協
- 適切な検証と品質ゲートなしで操作