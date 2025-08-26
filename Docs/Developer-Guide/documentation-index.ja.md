# SuperClaude Framework 開発者ガイド索引

## ドキュメントナビゲーションガイド

この索引は、効率的な情報発見のためにトピックとスキルレベル別に整理された、すべてのSuperClaude Framework開発ドキュメントへの包括的なアクセスを提供します。

### クイックナビゲーション

**新規貢献者向け**: [貢献ガイド → セットアップ](contributing-code.md#development-setup)から開始

**システム理解向け**: [技術アーキテクチャガイド → コンテキストアーキテクチャ](technical-architecture.md#context-file-architecture)から開始

**検証向け**: [検証ガイド → インストールチェック](testing-debugging.md#installation-verification)から開始

---

## 主要ドキュメント

### 📋 [コンテキストファイル貢献ガイド](contributing-code.md)
**目的**: 完全なコンテキストファイル開発と貢献ガイドライン  
**対象読者**: フレームワーク貢献者とコンテキストファイル開発者  
**長さ**: コンテキストファイルの現実に焦点を当てた約1,000行

**主要セクション**:
- [開発セットアップ](contributing-code.md#development-setup) - 環境設定と前提条件
- [コンテキストファイルガイドライン](contributing-code.md#context-file-guidelines) - 標準と構造
- [開発ワークフロー](contributing-code.md#development-workflow) - Gitワークフローと提出プロセス
- [コンポーネントへの貢献](contributing-code.md#contributing-to-components) - エージェント、コマンド、モード開発
- [ファイル検証](contributing-code.md#file-validation) - コンテキストファイル検証方法

### 🏗️ [コンテキストアーキテクチャガイド](technical-architecture.md)
**目的**: コンテキストファイルの動作と構造の理解  
**対象読者**: SuperClaudeを理解または拡張したいすべての人  
**長さ**: コンテキストファイルパターンとClaude Code統合に焦点を当てた約800行

**主要セクション**:
- [コンテキストファイルアーキテクチャ](technical-architecture.md#context-file-architecture) - ディレクトリ構造とファイル種類
- [インポートシステム](technical-architecture.md#the-import-system) - Claude Codeがコンテキストを読み込む方法
- [エージェントコンテキスト構造](technical-architecture.md#agent-context-structure) - ドメインスペシャリストコンテキスト
- [コマンドコンテキスト構造](technical-architecture.md#command-context-structure) - ワークフローパターン
- [Claude Codeがコンテキストを読み取る方法](technical-architecture.md#how-claude-code-reads-context) - 処理シーケンス
- [フレームワークの拡張](technical-architecture.md#extending-the-framework) - 新しいコンポーネントの追加

### 🧪 [検証・トラブルシューティングガイド](testing-debugging.md)
**目的**: インストール検証とコンテキストファイル問題のトラブルシューティング  
**対象読者**: ユーザーと保守担当者  
**長さ**: ファイル検証とClaude Code統合に焦点を当てた約500行

**主要セクション**:
- [インストール検証](testing-debugging.md#installation-verification) - コンテキストファイルインストール確認
- [コンテキストファイル検証](testing-debugging.md#context-file-verification) - ファイル構造検証
- [MCPサーバー検証](testing-debugging.md#mcp-server-verification) - 外部ツール設定
- [よくある問題](testing-debugging.md#common-issues) - 有効化問題のトラブルシューティング
- [トラブルシューティングコマンド](testing-debugging.md#troubleshooting-commands) - 診断手順

---

## トピック別索引

### 🚀 はじめに

**完全な初心者**:
1. [貢献ガイド → セットアップ](contributing-code.md#development-setup) - 環境セットアップ
2. [アーキテクチャガイド → 概要](technical-architecture.md#overview) - コンテキストファイルの理解
3. [検証ガイド → インストールチェック](testing-debugging.md#installation-verification) - 基本検証

**環境セットアップ**:
- [開発セットアップ](contributing-code.md#development-setup) - 前提条件と設定
- [インストール検証](testing-debugging.md#installation-verification) - ファイルインストール確認

### 🏗️ アーキテクチャと設計

**コンテキストファイルアーキテクチャ**:
- [コンテキストファイルアーキテクチャ](technical-architecture.md#context-file-architecture) - 完全なシステム設計
- [インポートシステム](technical-architecture.md#the-import-system) - Claude Codeがコンテキストを読み込む方法
- [エージェントコンテキスト構造](technical-architecture.md#agent-context-structure) - ドメインスペシャリストパターン
- [コマンドコンテキスト構造](technical-architecture.md#command-context-structure) - ワークフロー定義

**コンポーネント開発**:
- [コンポーネントへの貢献](contributing-code.md#contributing-to-components) - エージェント、コマンド、モード開発
- [新しいエージェントの追加](contributing-code.md#adding-new-agents) - ドメインスペシャリスト作成
- [新しいコマンドの追加](contributing-code.md#adding-new-commands) - ワークフローパターン開発
- [フレームワークの拡張](technical-architecture.md#extending-the-framework) - フレームワーク拡張

### 🧪 検証と品質

**ファイル検証**:
- [コンテキストファイル検証](testing-debugging.md#context-file-verification) - ファイル構造検証
- [ファイル検証](contributing-code.md#file-validation) - コンテキストファイル検証方法

**トラブルシューティング**:
- [よくある問題](testing-debugging.md#common-issues) - 有効化と設定問題
- [トラブルシューティングコマンド](testing-debugging.md#troubleshooting-commands) - 診断手順

### 🔧 開発ワークフロー

**コンテキストファイル開発**:
- [開発ワークフロー](contributing-code.md#development-workflow) - Gitワークフロー
- [コンテキストファイルガイドライン](contributing-code.md#context-file-guidelines) - 標準と実践
- [プルリクエストプロセス](contributing-code.md#pull-request-template) - 提出プロセス

**コンポーネント開発**:
- [エージェント開発](contributing-code.md#adding-new-agents) - ドメインスペシャリスト作成
- [コマンド開発](contributing-code.md#adding-new-commands) - ワークフローパターン作成
- [モード開発](contributing-code.md#adding-new-modes) - 動作変更パターン

### 🛠️ MCP統合

**MCP設定**:
- [MCPサーバー設定](technical-architecture.md#mcp-server-configuration) - 外部ツールセットアップ
- [MCPサーバー検証](testing-debugging.md#mcp-server-verification) - 設定検証

### 🚨 サポートとトラブルシューティング

**よくある問題**:
- [コマンドが動作しない](testing-debugging.md#issue-commands-not-working) - コンテキストトリガー問題
- [エージェントが有効化されない](testing-debugging.md#issue-agents-not-activating) - 有効化問題
- [コンテキストが読み込まれない](testing-debugging.md#issue-context-not-loading) - 読み込み問題

**サポートリソース**:
- [ヘルプの入手](contributing-code.md#getting-help) - サポートチャンネル
- [問題報告](contributing-code.md#issue-reporting) - バグ報告と機能

---

## スキルレベル別パス

### 🟢 初心者パス（SuperClaudeの理解）

**第1週: 基礎**
1. [アーキテクチャ概要](technical-architecture.md#overview) - SuperClaudeとは
2. [インストール検証](testing-debugging.md#installation-verification) - セットアップ確認
3. [コンテキストファイルアーキテクチャ](technical-architecture.md#context-file-architecture) - ディレクトリ構造

**第2週: 基本使用**
1. [Claude Codeがコンテキストを読み取る方法](technical-architecture.md#how-claude-code-reads-context) - 処理シーケンス
2. [よくある問題](testing-debugging.md#common-issues) - トラブルシューティング基本
3. [コンテキストファイルガイドライン](contributing-code.md#context-file-guidelines) - ファイル標準

### 🟡 中級パス（コンテキストファイル貢献）

**第1か月: コンテキスト開発**
1. [開発セットアップ](contributing-code.md#development-setup) - 環境準備
2. [エージェントコンテキスト構造](technical-architecture.md#agent-context-structure) - ドメインスペシャリスト
3. [コマンドコンテキスト構造](technical-architecture.md#command-context-structure) - ワークフローパターン

**第2か月: コンポーネント作成**
1. [新しいエージェントの追加](contributing-code.md#adding-new-agents) - ドメインスペシャリスト開発
2. [新しいコマンドの追加](contributing-code.md#adding-new-commands) - ワークフロー作成
3. [ファイル検証](contributing-code.md#file-validation) - コンテキスト検証

### 🔴 上級パス（フレームワーク拡張）

**高度な理解**
1. [インポートシステム](technical-architecture.md#the-import-system) - コンテキスト読み込み仕組み
2. [フレームワークの拡張](technical-architecture.md#extending-the-framework) - フレームワーク拡張
3. [MCPサーバー設定](technical-architecture.md#mcp-server-configuration) - 外部ツール統合

---

## 参考資料

### 📚 主要概念

**フレームワークの基礎**:
- コンテキスト指向設定フレームワーク
- エージェントドメインスペシャリスト  
- コマンドワークフローパターン
- モード動作変更
- MCP統合パターン

### 🔗 相互参照

**開発 → アーキテクチャ**:
- [コンテキストファイルガイドライン](contributing-code.md#context-file-guidelines) → [コンテキストファイルアーキテクチャ](technical-architecture.md#context-file-architecture)
- [コンポーネント追加](contributing-code.md#contributing-to-components) → [エージェント・コマンド構造](technical-architecture.md#agent-context-structure)

**開発 → 検証**:
- [開発ワークフロー](contributing-code.md#development-workflow) → [ファイル検証](testing-debugging.md#context-file-verification)
- [ファイル検証](contributing-code.md#file-validation) → [インストール検証](testing-debugging.md#installation-verification)

**アーキテクチャ → 検証**:
- [Claude Codeがコンテキストを読み取る方法](technical-architecture.md#how-claude-code-reads-context) → [トラブルシューティング](testing-debugging.md#common-issues)
- [MCP設定](technical-architecture.md#mcp-server-configuration) → [MCP検証](testing-debugging.md#mcp-server-verification)

---

## 品質標準

### ✅ ドキュメント精度
- **技術的精度**: すべての例がSuperClaudeの現実を反映（コンテキストファイル、ソフトウェアではない）
- **コマンド精度**: 正しいPythonモジュール実行パスとClaude Codeコンテキストトリガー
- **フィクションなし**: 存在しないテストフレームワークとパフォーマンスシステムへの言及をすべて削除

### ✅ コンテンツ焦点
- **コンテキストファイル**: ドキュメントは .md 指示ファイルとClaude Code動作に焦点
- **ファイル検証**: コンテキストファイルインストールと構造検証への実用的アプローチ
- **実際のワークフロー**: コンテキストファイル貢献のための実際の開発プロセス

### ✅ ユーザーエクスペリエンス
- **明確な進行**: 理解から貢献まで、スキルベースの学習パス
- **実用的な例**: 動作するコンテキストファイル例とClaude Code統合
- **サポート統合**: 実際の問題に対するヘルプリソースへの明確な案内

---

## 使用ガイドライン

### 貢献者向け
1. **開始**: [開発セットアップ](contributing-code.md#development-setup)
2. **コンテキスト開発**: [コンテキストファイルガイドライン](contributing-code.md#context-file-guidelines)に従う
3. **検証**: [ファイル検証](contributing-code.md#file-validation)を使用
4. **サポート**: [ヘルプの入手](contributing-code.md#getting-help)を参照

### アーキテクト向け
1. **システム理解**: [コンテキストファイルアーキテクチャ](technical-architecture.md#context-file-architecture)
2. **コンポーネントパターン**: [エージェントとコマンド構造](technical-architecture.md#agent-context-structure)
3. **拡張**: [フレームワークの拡張](technical-architecture.md#extending-the-framework)
4. **統合**: [MCP設定](technical-architecture.md#mcp-server-configuration)

### 検証向け
1. **インストール確認**: [インストール検証](testing-debugging.md#installation-verification)
2. **ファイル検証**: [コンテキストファイル検証](testing-debugging.md#context-file-verification)
3. **トラブルシューティング**: [よくある問題](testing-debugging.md#common-issues)
4. **診断**: [トラブルシューティングコマンド](testing-debugging.md#troubleshooting-commands)

この包括的な索引は、SuperClaudeをコンテキスト指向設定フレームワークとしての現実を反映し、実用的なコンテキストファイル開発とClaude Code統合に焦点を当てています。