# SuperClaude Framework にコンテキストファイルを貢献する 🛠️

SuperClaude Framework 開発へようこそ！このガイドでは、構造化されたプロンプトとMCPサーバー統合を通じてClaude Codeを強化するコンテキストファイルと動作指示を貢献するために必要なすべてを提供します。

**プロジェクトの目的**: SuperClaudeは、Claude Codeに構造化されたコンテキストファイルと動作指示を提供します。私たちは、インテリジェントなプロンプトエンジニアリングを通じてAI支援開発の次世代を構築しています。

## 目次

1. [開発セットアップ](#開発セットアップ) - 前提条件と環境
2. [アーキテクチャ概要](#アーキテクチャ概要) - システムコンポーネントと設計  
3. [コンテキストファイルガイドライン](#コンテキストファイルガイドライン) - 標準と実践
4. [開発ワークフロー](#開発ワークフロー) - Gitワークフローと提出
5. [コンポーネントへの貢献](#コンポーネントへの貢献) - エージェント、コマンド、モード
6. [ファイル検証](#ファイル検証) - 品質保証
7. [ヘルプの入手](#ヘルプの入手) - サポートとリソース

## 開発セットアップ

### 前提条件

**必須:**
- Python 3.8+ with pip
- Git for version control
- Claude Code インストール済みで動作
- Node.js 16+ (MCP サーバー設定用)

**環境セットアップ:**
```bash
# 最初にGitHubでSuperClaude_Frameworkをフォーク
git clone https://github.com/YOUR_USERNAME/SuperClaude_Framework.git
cd SuperClaude_Framework

# インストールシステムをテスト
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup --help

# 開発場所にインストール
PYTHONPATH=/path/to/SuperClaude_Framework python3 -m setup install --components core
```

**検証チェック:**
```bash
# Pythonバージョン確認
python3 --version  # 3.8+ である必要があります

# MCP設定用Node.jsチェック
node --version     # 16+ である必要があります

# Claude Code統合テスト
ls ~/.claude/      # Claude Codeディレクトリが表示される必要があります
```

## アーキテクチャ概要

### フレームワーク構造

SuperClaudeは **コンテキスト指向設定フレームワーク** です - 実行されるソフトウェアではなく、Claude Codeが動作を変更するために読み取る指示ファイルです。

```
SuperClaude_Framework/
├── SuperClaude/           # フレームワークコンポーネント（信頼できる情報源）
│   ├── Core/             # PRINCIPLES.md、RULES.md、FLAGS.md
│   ├── Agents/           # 15の専門ドメインエキスパート
│   ├── Commands/         # 21のコンテキストトリガーパターン（/sc: 動作指示）
│   ├── Modes/            # 6の動作変更パターン
│   └── MCP/              # 6つのMCPサーバー設定
├── setup/                # Pythonインストールシステム
├── Docs/                 # ドキュメント（現在読んでいるもの）
└── tests/                # ファイル検証スクリプト
```

**主要概念:**
- **コンテキストファイル**: Claude Codeの動作をガイドする .md 指示ファイル
- **エージェント**: ドメインスペシャリスト（例：security-engineer.md、python-expert.md）  
- **コマンド**: ワークフローパターン（例：implement.md、analyze.md）
- **モード**: インタラクション修飾子（例：brainstorming、introspection）
- **MCP統合**: Model Context Protocolサーバーの設定

### 動作原理

```
ユーザー入力 → Claude Code → SuperClaudeコンテキストを読取 → 修正された動作 → 強化された出力
```

1. ユーザーが **Claude Code会話で**（ターミナルではなく）`/sc:implement "auth system"` と入力
2. Claude Code が `SuperClaude/Commands/implement.md` を読取
3. コマンドがsecurity-engineerエージェントコンテキストを有効化
4. Context7 MCPが認証パターンを提供
5. Claudeが完全で安全な実装を生成

## コンテキストファイルガイドライン

### ファイル構成

**コンテキストファイル（`.md`）:**
- Claude Code用の明確で実行可能な指示を記述
- 設定用のfrontmatterメタデータを使用  
- 既存のパターンと命名規則に従う
- 指示が期待される動作を生成することをテスト

**インストールスクリプト（`.py`）:**
- PEP 8 スタイルガイドラインに従う
- 関数とクラスにdocstringsを含める
- 有益な場合は型ヒントを追加
- ファイルコピーと設定に焦点を当てる

**エージェント構造の例:**
```markdown
---
name: new-specialist
description: 専門知識の簡潔な説明
category: specialized|architecture|quality
tools: Read, Write, Edit, Bash, Grep
---

# エージェント名

## トリガー
- このエージェントを有効化するキーワード
- 有効化をトリガーするファイル種類

## 動作マインドセット
コアフィロソフィーとアプローチ

## 焦点領域
- ドメイン専門知識領域1
- ドメイン専門知識領域2

## 主要アクション
1. 特定の動作パターン
2. 問題解決アプローチ
```

### コンテキストファイル標準

**構造要件:**
- Claude Code用の明確で実行可能な指示
- 特定のトリガーと有効化パターン
- 使用方法を実証する例
- 範囲を定義する境界

**品質標準:**
- 指示は Claude Code 会話でテスト可能
- 例は期待される動作変更を生成
- 明確な有効化トリガーとコンテキストパターン
- プロフェッショナルな言語とフォーマット

## 開発ワークフロー

### Git ワークフロー

1. **フォークとクローン:**
   ```bash
   # GitHubでフォークしてから:
   git clone https://github.com/YOUR_USERNAME/SuperClaude_Framework.git
   cd SuperClaude_Framework
   git remote add upstream https://github.com/SuperClaude-Org/SuperClaude_Framework.git
   ```

2. **機能ブランチ作成:**
   ```bash
   git checkout -b feature/your-feature-name
   # 変更作業
   git add .
   git commit -m "Add: 説明的なコミットメッセージ"
   ```

3. **プルリクエスト提出:**
   ```bash
   git push origin feature/your-feature-name
   # GitHubでPRを作成
   ```

### プルリクエストテンプレート

```markdown
## 説明
コンテキストファイル変更の簡潔な説明

## 変更の種類
- [ ] コンテキストファイルのバグ修正
- [ ] 新機能（エージェント、コマンド、モード）
- [ ] ドキュメント改善
- [ ] インストールシステム強化

## テスト
- [ ] Claude Codeでの手動テスト
- [ ] コンテキストファイル検証パス
- [ ] Claude Code会話での例の検証

## チェックリスト
- [ ] ファイルがSuperClaudeの規約に従っている
- [ ] セルフレビュー完了
- [ ] ドキュメント更新済み
- [ ] 既存コンテキストへの破壊的変更なし
```

### コードレビュープロセス

**手動レビュー:**
- コンテキストファイルの明確性と効果性
- エージェント・コマンドロジックとトリガー  
- ドキュメントの正確性と完全性
- 既存コンポーネントとの統合
- Claude Code 動作テスト結果

## コンポーネントへの貢献

### 新しいエージェントの追加

**エージェント開発プロセス:**
1. ドメイン専門知識のギャップを特定
2. `SuperClaude/Agents/` にエージェントファイルを作成
3. トリガー、動作、境界を定義
4. 様々なClaude Codeシナリオでテスト
5. 使用パターンと例をドキュメント化

**エージェントテンプレート:**
```markdown
---
name: agent-name
description: ドメイン専門知識の説明
category: specialized
tools: Read, Write, Edit, Bash
---

# エージェント名

## トリガー
- 特定のキーワード: domain、expertise、area
- ファイルパターン: *.domain、特定のフレームワーク
- 複雑度指標: アーキテクチャの決定

## 動作マインドセット
- ドメインのベストプラクティスに焦点
- 問題解決への体系的アプローチ
- 品質とセキュリティの考慮

## 焦点領域
- コアドメイン専門知識
- 関連技術領域
- 統合パターン

## 主要アクション
1. ドメインコンテキスト内で要件を分析
2. ドメイン固有のベストプラクティスを適用
3. 関連専門家と連携
4. ソリューションがドメイン標準を満たすことを検証
```

### 新しいコマンドの追加

**コマンド構造:**
```markdown
---
name: command-name
description: コマンドの目的
category: workflow|utility|analysis
complexity: basic|standard|advanced
mcp-servers: [context7, sequential]
personas: [architect, engineer]
---

# /sc:command-name

## トリガー
- このコマンドを使用する場合
- コンテキストインジケーター

## 使用方法
Claude Code会話で入力:
```
/sc:command-name [target] [--options]
```
**注意**: これはコンテキストトリガーパターンであり、ターミナルコマンドではありません。

## ワークフローパターン
1. 初期分析
2. 処理ステップ  
3. 検証と出力

## 例
実用的な使用例
```

### 新しいモードの追加

**モード開発:**
- 有効化トリガーを定義
- 動作修正を指定
- インタラクションパターンを作成
- 異なるClaude Codeシナリオでテスト

## ファイル検証

### コンテキストファイル検証

**手動検証プロセス:**
1. Claude Codeに開発版をインストール
2. Claude Code会話でエージェント・コマンド有効化トリガーをテスト
3. 期待通りの動作修正が発生することを確認
4. コンテキストファイル構造とフォーマットを検証
5. エッジケースとエラー条件をテスト

**検証チェックリスト:**
- [ ] コンテキストファイルが有効なmarkdown構文を使用
- [ ] Claude Codeでトリガーが正しく有効化
- [ ] 動作がドキュメントと一致
- [ ] 既存コンポーネントとの競合なし
- [ ] Claude Code会話で例が期待される結果を生成

### ファイル構造検証

```bash
# ファイル構造確認
find ~/.claude -name "*.md" | head -10

# コンテキストファイル形式検証
head ~/.claude/agents/python-expert.md

# インポートシステムテスト
grep "@import" ~/.claude/CLAUDE.md
```

## ヘルプの入手

### 開発サポート

**ドキュメント:**
- [技術アーキテクチャ](technical-architecture.md) - システム設計詳細  
- [検証ガイド](testing-debugging.md) - ファイル検証手順

**コミュニティチャンネル:**
- GitHub Issues: バグ報告と機能リクエスト
- GitHub Discussions: 開発質問とアイデア
- プルリクエストレビュー: コンテキストファイルフィードバックと協力

**コードレビューガイドライン:**
- 建設的で具体的なフィードバックを提供
- 可能な場合は変更をローカルでテスト
- 保守性と明確性に焦点
- 貢献者の努力と学習を尊重

### 問題報告

**バグ報告:**
1. Claude Codeでの期待される動作vs実際の動作を記述
2. コンテキストトリガーでの再現手順を提供
3. 環境詳細とファイルバージョンを含める
4. 関連するコンテキストファイル設定を共有

**機能リクエスト:**
1. 提案される動作強化を説明
2. ユーザーがどのように利益を得るかを記述
3. 既存のコンテキストパターンとの統合を考慮
4. 使用例を提供

## 貢献ガイドラインのまとめ

### すべきこと
✅ **既存のパターンと規約に従う**
✅ **Claude Codeでコンテキストファイルを徹底的にテスト**
✅ **明確で実行可能な動作指示を記述**  
✅ **動作する例を提供**
✅ **ユーザーエクスペリエンス向上に焦点**
✅ **関連コンポーネントと連携**

### してはいけないこと
❌ **既存機能を壊さない**
❌ **テストされていないコンテキスト変更を追加しない**
❌ **スタイルガイドラインを無視しない**
❌ **過度に複雑な動作パターンを作成しない**
❌ **既存機能を重複させない**

### 品質標準

**コンテキストファイル:**
- 明確な有効化トリガー
- 特定の動作指示
- 実用的な例
- 定義された範囲境界

**ドキュメント:**
- 正確で最新
- 動作するコンテキスト例
- 明確なナビゲーション構造
- アクセシビリティ考慮

## ライセンスと帰属

**MITライセンス**: SuperClaude Frameworkは、使用、修正、配布の最大の自由を提供するMITライセンスの下でライセンスされています。

SuperClaude Frameworkに貢献することで、あなたの貢献が同じMITライセンスの下でライセンスされることに同意します。コンテキストファイルを使用、修正、配布するための永続的権利をプロジェクトに付与しながら、あなたは貢献に対する著作権を保持します。

## 謝辞

SuperClaude Frameworkは、AI支援開発の進歩を信じる開発者、ユーザー、貢献者の協力的努力のおかげで存在しています。すべてのバグ報告、機能提案、ドキュメント改善、コンテキストファイル貢献により、フレームワークは全員にとってより良いものになります。

あなたの専門知識と視点により、SuperClaude Frameworkはより良いものになります。コンテキストファイルの改善、機能の追加、他のユーザーの支援のいずれを行うにしても、すべての貢献は、より効果的なAI支援開発という目標を前進させます。

---

**SuperClaude Framework 貢献者コミュニティへようこそ！** あなたの貢献は、インテリジェントなコンテキストと行動プログラミングを通じてAI支援開発の未来を構築するのに役立ちます。