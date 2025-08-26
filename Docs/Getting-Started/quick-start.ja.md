<div align="center">

# 🚀 SuperClaude クイックスタートガイド

### **Claude Codeのためのコンテキストエンジニアリングフレームワーク**

<p align="center">
  <img src="https://img.shields.io/badge/Framework-Context_Engineering-purple?style=for-the-badge" alt="Framework">
  <img src="https://img.shields.io/badge/Version-4.0.8-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Time_to_Start-5_Minutes-green?style=for-the-badge" alt="Quick Start">
</p>

> **💡 重要な洞察**: SuperClaudeはClaude Codeを置き換えるのではなく、行動コンテキストの注入を通じて**設定と強化**を行います

<p align="center">
  <a href="#-仕組み">仕組み</a> •
  <a href="#-即座に開始">即座に開始</a> •
  <a href="#-コアコンポーネント">コンポーネント</a> •
  <a href="#-ワークフローパターン">ワークフロー</a> •
  <a href="#-いつ使うか">いつ使うか</a>
</p>

</div>

---

<div align="center">

## 📊 **フレームワーク機能**

| **コマンド** | **AIエージェント** | **動作モード** | **MCPサーバー** |
|:------------:|:-------------:|:-------------------:|:---------------:|
| **21個** | **14個** | **6個** | **6個** |
| `/sc:` トリガー | ドメイン専門家 | コンテキスト適応 | ツール統合 |

</div>

---

## 🎯 **仕組み**

<div align="center">

### **フレームワークアーキテクチャフロー**

```
┌─────────────────┐     ┌──────────────────┐     ┌─────────────────┐
│  ユーザー入力    │────>│   Claude Code    │────>│  コンテキスト    │
│  /sc:command    │     │  コンテキスト読込  │     │ ファイル(.md)   │
└─────────────────┘     └──────────────────┘     └─────────────────┘
                               │                          │
                               ▼                          ▼
┌─────────────────┐      ┌──────────────────┐     ┌─────────────────┐
│   強化された     │<─────│    動作の        │<────│   MCPサーバー   │
│   レスポンス     │      │    アクティブ化   │     │  （設定済み）   │
└─────────────────┘      └──────────────────┘     └─────────────────┘
```

**魔法の仕組み**: `/sc:brainstorm`と入力すると、Claudeがインストールされた`.md`ファイルから行動指示を読み込み、強化された能力で応答します

</div>

---

## ⚡ **即座に開始**

<div align="center">

### **インストールから最初のコマンドまで5分**

</div>

<table>
<tr>
<th width="50%">📦 ステップ1: インストール（ターミナル）</th>
<th width="50%">💬 ステップ2: 使用（Claude Code）</th>
</tr>
<tr>
<td valign="top">

```bash
# pipxでクイックインストール
pipx install SuperClaude && SuperClaude install

# または従来のpip
pip install SuperClaude && SuperClaude install

# またはnpm経由
npm install -g @bifrost_inc/superclaude && superclaude install
```

</td>
<td valign="top">

```text
# インタラクティブ発見
/sc:brainstorm "タスク管理のWebアプリ"

# 既存コードを分析
/sc:analyze src/

# 実装を生成
/sc:implement "ユーザー認証"

# 専門家を起動
@agent-security "認証フローをレビュー"
```

</td>
</tr>
</table>

<details>
<summary><b>🎥 舞台裏で起こること</b></summary>

1. **コンテキスト読み込み**: Claude Codeが`CLAUDE.md`経由で行動`.md`ファイルをインポート
2. **パターン認識**: `/sc:`と`@agent-`トリガーパターンを認識
3. **行動の活性化**: コンテキストファイルから対応する指示を適用
4. **MCP統合**: 利用可能な場合は設定された外部ツールを使用
5. **レスポンス強化**: 包括的な応答のためのフレームワークパターンに従う

</details>

---

## 🔧 **コアコンポーネント**

<div align="center">

### **SuperClaudeの4つの柱**

<table>
<tr>
<td align="center" width="25%">

### 📝 **コマンド**
<h2>21個</h2>

**スラッシュコマンド**

`/sc:brainstorm`  
`/sc:implement`  
`/sc:analyze`  
`/sc:workflow`

*ワークフロー自動化*

</td>
<td align="center" width="25%">

### 🤖 **エージェント**
<h2>14個</h2>

**AI専門家**

`@agent-architect`  
`@agent-security`  
`@agent-frontend`  
`@agent-backend`

*ドメイン専門知識*

</td>
<td align="center" width="25%">

### 🎯 **モード**
<h2>6個</h2>

**動作モード**

ブレインストーミング  
内省  
オーケストレーション  
タスク管理

*コンテキスト適応*

</td>
<td align="center" width="25%">

### 🔌 **MCP**
<h2>6個</h2>

**サーバー統合**

Context7（ドキュメント）  
Sequential（分析）  
Magic（UI）  
Playwright（テスト）

*強化されたツール*

</td>
</tr>
</table>

</div>

---

## 📚 **ワークフローパターン**

<div align="center">

### **完全な開発ライフサイクル**

</div>

### **🌟 初回プロジェクトセッション**

<table>
<tr>
<th>ステップ</th>
<th>コマンド</th>
<th>何が起こるか</th>
</tr>
<tr>
<td><b>1. 発見</b></td>
<td><code>/sc:brainstorm "eコマースアプリ"</code></td>
<td>インタラクティブな要件探索</td>
</tr>
<tr>
<td><b>2. コンテキスト読み込み</b></td>
<td><code>/sc:load src/</code></td>
<td>既存プロジェクト構造をインポート</td>
</tr>
<tr>
<td><b>3. 分析</b></td>
<td><code>/sc:analyze --focus architecture</code></td>
<td>アーキテクチャの詳細レビュー</td>
</tr>
<tr>
<td><b>4. 計画</b></td>
<td><code>/sc:workflow "決済統合"</code></td>
<td>実装ロードマップを生成</td>
</tr>
<tr>
<td><b>5. 実装</b></td>
<td><code>/sc:implement "Stripeチェックアウト"</code></td>
<td>ベストプラクティスでビルド</td>
</tr>
<tr>
<td><b>6. 検証</b></td>
<td><code>/sc:test --coverage</code></td>
<td>包括的テスト</td>
</tr>
<tr>
<td><b>7. セッション保存</b></td>
<td><code>/sc:save "決済完了"</code></td>
<td>次のセッションのために保持</td>
</tr>
</table>

### **🎨 ドメイン特化ワークフロー**

<div align="center">

| ドメイン | トリガー | 専門家活性化 | MCPサーバー |
|--------|---------|----------------------|------------|
| **フロントエンド** | UIコンポーネント要求 | `@agent-frontend` | Magic |
| **バックエンド** | APIエンドポイント作成 | `@agent-backend` | Sequential |
| **セキュリティ** | 認証実装 | `@agent-security` | Context7 |
| **テスト** | E2Eテストシナリオ | `@agent-qa` | Playwright |
| **DevOps** | デプロイメント設定 | `@agent-devops` | Morphllm |

</div>

---

## 🎯 **いつ使うか**

<div align="center">

### **SuperClaude vs 標準Claude Code**

<table>
<tr>
<th width="50%">✅ SuperClaudeを使用</th>
<th width="50%">💭 標準Claudeを使用</th>
</tr>
<tr>
<td valign="top">

**最適な場面:**
- 🏗️ 完全なソフトウェアプロジェクトの構築
- 📊 品質ゲートを持つ体系的なワークフロー
- 🔄 複雑なマルチコンポーネントシステム
- 💾 永続化が必要な長期プロジェクト
- 👥 標準を持つチームコラボレーション
- 🎯 ドメイン特化の専門知識が必要

**例:**
- 「フルスタックアプリケーションを構築」
- 「セキュアな認証を実装」
- 「レガシーコードベースをリファクタリング」
- 「包括的テストスイートを作成」

</td>
<td valign="top">

**向いている場面:**
- 💡 シンプルな質問や説明
- ⚡ 一回限りのコーディングタスク
- 📚 プログラミング概念の学習
- 🧪 クイックプロトタイプや実験
- 🔍 コードスニペット生成
- ❓ 一般的なプログラミングヘルプ

**例:**
- 「async/awaitの仕組みを説明」
- 「ソート関数を書く」
- 「このエラーメッセージをデバッグ」
- 「このループを関数型に変換」

</td>
</tr>
</table>

</div>

---

## 🎓 **学習パス**

<div align="center">

### **マスタリーまでの4週間ジャーニー**

<table>
<tr>
<th>週</th>
<th>フォーカス</th>
<th>スキル</th>
<th>マイルストーン</th>
</tr>
<tr>
<td align="center"><b>1</b><br/>🌱</td>
<td><b>コアコマンド</b></td>
<td>
• <code>/sc:brainstorm</code><br/>
• <code>/sc:analyze</code><br/>
• <code>/sc:implement</code>
</td>
<td>最初のプロジェクトを完成</td>
</tr>
<tr>
<td align="center"><b>2</b><br/>🌿</td>
<td><b>動作モード</b></td>
<td>
• モード組み合わせ<br/>
• フラグ使用法<br/>
• コンテキスト最適化
</td>
<td>ワークフロー最適化</td>
</tr>
<tr>
<td align="center"><b>3</b><br/>🌿</td>
<td><b>MCPサーバー</b></td>
<td>
• サーバー設定<br/>
• ツール統合<br/>
• 強化された機能
</td>
<td>フルツール活用</td>
</tr>
<tr>
<td align="center"><b>4</b><br/>🌲</td>
<td><b>高度なパターン</b></td>
<td>
• カスタムワークフロー<br/>
• セッション管理<br/>
• チームパターン
</td>
<td>フレームワークマスタリー</td>
</tr>
</table>

</div>

---

## 💡 **主な洞察**

<div align="center">

### **SuperClaudeの価値を理解する**

<table>
<tr>
<td width="33%" align="center">

### 🧠 **ソフトウェアではない**
**フレームワークです**

SuperClaudeは行動設定であり、独立したソフトウェアではありません。すべてはClaude Code経由で実行されます。

</td>
<td width="33%" align="center">

### 🔄 **体系的**
**アドホックではない**

ランダムなリクエストを、品質ゲートと検証を持つ構造化されたワークフローに変換します。

</td>
<td width="33%" align="center">

### 🚀 **段階的**
**複雑ではない**

基本コマンドからシンプルに始めます。複雑さは必要に応じて自然に現れます。

</td>
</tr>
</table>

</div>

---

## 📖 **次のステップ**

<div align="center">

### **学習ジャーニーを続ける**

<table>
<tr>
<th>🌱 初心者</th>
<th>🌿 中級者</th>
<th>🌲 上級者</th>
</tr>
<tr>
<td valign="top">

**最初の週:**
- [インストールガイド](installation.md)
- [コマンドリファレンス](../User-Guide/commands.md)
- [例のクックブック](../Reference/examples-cookbook.md)

`/sc:brainstorm`から始める

</td>
<td valign="top">

**スキル向上:**
- [動作モード](../User-Guide/modes.md)
- [エージェントガイド](../User-Guide/agents.md)
- [セッション管理](../User-Guide/session-management.md)

モード組み合わせを探索

</td>
<td valign="top">

**エキスパート使用法:**
- [MCPサーバー](../User-Guide/mcp-servers.md)
- [技術アーキテクチャ](../Developer-Guide/technical-architecture.md)
- [貢献](../Developer-Guide/contributing-code.md)

カスタムワークフロー作成

</td>
</tr>
</table>

<p align="center">
  <a href="../User-Guide/commands.md">
    <img src="https://img.shields.io/badge/📚_探索-全21コマンド-blue?style=for-the-badge" alt="Commands">
  </a>
  <a href="../Reference/examples-cookbook.md">
    <img src="https://img.shields.io/badge/🍳_試す-実例-green?style=for-the-badge" alt="Examples">
  </a>
</p>

</div>

---

<div align="center">

### **🎉 開発ワークフローを変革する準備はできましたか？**

<p align="center">
  <b>Claude Codeで</b> <code>/sc:brainstorm</code> <b>を使って今すぐ始めましょう！</b>
</p>

<p align="center">
  <sub>SuperClaude v4.0.8 - Claude Codeのためのコンテキストエンジニアリング</sub>
</p>

</div>