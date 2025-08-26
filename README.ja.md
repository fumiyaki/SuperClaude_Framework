<div align="center">

# 🚀 SuperClaude フレームワーク

### **Claude Codeを構造化された開発プラットフォームに変革**

<p align="center">
  <img src="https://img.shields.io/badge/version-4.0.8-blue" alt="Version">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License">
  <img src="https://img.shields.io/badge/PRs-welcome-brightgreen.svg" alt="PRs Welcome">
</p>

<p align="center">
  <a href="https://superclaude.netlify.app/">
    <img src="https://img.shields.io/badge/🌐_ウェブサイトへ-blue" alt="Website">
  </a>
  <a href="https://pypi.org/project/SuperClaude/">
    <img src="https://img.shields.io/pypi/v/SuperClaude.svg?" alt="PyPI">
  </a>
  <a href="https://www.npmjs.com/package/@bifrost_inc/superclaude">
    <img src="https://img.shields.io/npm/v/@bifrost_inc/superclaude.svg" alt="npm">
  </a>
</p>

<p align="center">
  <a href="#-クイックインストール">クイックスタート</a> •
  <a href="#-プロジェクトのサポート">サポート</a> •
  <a href="#-v4の新機能">機能</a> •
  <a href="#-ドキュメント">ドキュメント</a> •
  <a href="#-貢献">貢献</a>
</p>

</div>

---

<div align="center">

## 📊 **フレームワーク統計**

| **コマンド** | **エージェント** | **モード** | **MCPサーバー** |
|:------------:|:----------:|:---------:|:---------------:|
| **21** | **14** | **5** | **6** |
| スラッシュコマンド | 専門AI | 行動パターン | インテグレーション |

</div>

---

<div align="center">

## 🎯 **概要**

SuperClaudeは**メタプログラミング設定フレームワーク**で、行動指示インジェクションとコンポーネントオーケストレーションを通じてClaude Codeを構造化された開発プラットフォームに変革します。強力なツールとインテリジェントなエージェントによるシステマチックなワークフロー自動化を提供します。

## ⚡ **クイックインストール**

### **インストール方法を選択**

| 方法 | コマンド | 最適用途 |
|:------:|---------|----------|
| **🐍 pipx** | `pipx install SuperClaude && pipx upgrade SuperClaude && SuperClaude install` | **✅ 推奨** - Linux/macOS |
| **📦 pip** | `pip install SuperClaude && pip upgrade SuperClaude && SuperClaude install` | 従来のPython環境 |
| **🌐 npm** | `npm install -g @bifrost_inc/superclaude && superclaude install` | クロスプラットフォーム、Node.jsユーザー |

</div>

<details>
<summary><b>⚠️ 重要：SuperClaude V3からのアップグレード</b></summary>

**SuperClaude V3がインストールされている場合は、V4をインストールする前にアンインストールしてください：**

```bash
# まずV3をアンインストール
関連するすべてのファイルとディレクトリを削除:
*.md *.json および commands/

# その後V4をインストール
pipx install SuperClaude && pipx upgrade SuperClaude && SuperClaude install
```

**✅ アップグレード時に保持される項目：**
- ✓ カスタムスラッシュコマンド（`commands/sc/`外）
- ✓ `CLAUDE.md`のカスタムコンテンツ
- ✓ Claude Codeの`.claude.json`、`.credentials.json`、`settings.json`、`settings.local.json`
- ✓ 追加したカスタムエージェントとファイル

**⚠️ 注意：** V3の他のSuperClaude関連`.json`ファイルは競合を起こす可能性があるため削除してください。

</details>

<details>
<summary><b>💡 PEP 668エラーのトラブルシューティング</b></summary>

```bash
# オプション1：pipxを使用（推奨）
pipx install SuperClaude

# オプション2：ユーザーインストール
pip install --user SuperClaude

# オプション3：強制インストール（注意して使用）
pip install --break-system-packages SuperClaude
```
</details>

---

<div align="center">

## 💖 **プロジェクトのサポート**

> 正直に言うと、SuperClaudeの維持には時間とリソースが必要です。
> 
> *テスト用のClaude Maxサブスクリプションだけで月額100ドルかかり、これはドキュメント作成、バグ修正、機能開発にかける時間を計算に入れる前の話です。*
> *SuperClaudeが日々の作業に価値を提供しているなら、プロジェクトへのサポートをご検討ください。*
> *わずかな金額でも基本的な費用をカバーし、開発を継続的に保つのに役立ちます。*
> 
> コード、フィードバック、サポートのいずれでも、すべての貢献者が重要です。このコミュニティの一員でいてくれてありがとう！ 🙏

<table>
<tr>
<td align="center" width="33%">
  
### ☕ **Ko-fi**
[![Ko-fi](https://img.shields.io/badge/Support_on-Ko--fi-ff5e5b?logo=ko-fi)](https://ko-fi.com/superclaude)

*一回限りの貢献*

</td>
<td align="center" width="33%">

### 🎯 **Patreon**
[![Patreon](https://img.shields.io/badge/Become_a-Patron-f96854?logo=patreon)](https://patreon.com/superclaude)

*月額サポート*

</td>
<td align="center" width="33%">

### 💜 **GitHub**
[![GitHub Sponsors](https://img.shields.io/badge/GitHub-Sponsor-30363D?logo=github-sponsors)](https://github.com/sponsors/SuperClaude-Org)

*柔軟なティア*

</td>
</tr>
</table>

### **あなたのサポートが可能にすること：**

| 項目 | コスト/インパクト |
|------|-------------|
| 🔬 **Claude Maxテスト** | 検証とテストのため月額100ドル |
| ⚡ **機能開発** | 新機能と改善 |
| 📚 **ドキュメント** | 包括的なガイドと例 |
| 🤝 **コミュニティサポート** | 迅速な問題対応とヘルプ |
| 🔧 **MCP統合** | 新しいサーバー接続のテスト |
| 🌐 **インフラ** | ホスティングとデプロイメントコスト |

> **注意：** でもプレッシャーに感じる必要はありません - フレームワークはどちらにせよオープンソースであり続けます。ただ、人々が使用し、評価してくれていることを知るのは励みになります。コード、ドキュメンテーション、または宣伝での貢献も助けになります！ 🙏

</div>

---

<div align="center">

## 🎉 **V4の新機能**

> *バージョン4では、コミュニティフィードバックと実際の使用パターンに基づいて大幅な改善が行われました。*

<table>
<tr>
<td width="50%">

### 🤖 **よりスマートなエージェントシステム**
**14の専門エージェント**とドメインエキスパート：
- セキュリティエンジニアが実際の脆弱性をキャッチ
- フロントエンドアーキテクトがUIパターンを理解
- コンテキストに基づく自動調整
- オンデマンドのドメイン固有専門知識

</td>
<td width="50%">

### 📝 **改善された名前空間**
すべてのコマンドに**`/sc:`プレフィックス**：
- カスタムコマンドとの競合なし
- 全ライフサイクルをカバーする21コマンド
- ブレインストーミングからデプロイメントまで
- 清潔で整理されたコマンド構造

</td>
</tr>
<tr>
<td width="50%">

### 🔧 **MCPサーバー統合**
連携する**6つの強力なサーバー**：
- **Context7** → 最新のドキュメント
- **Sequential** → 複雑な分析
- **Magic** → UIコンポーネント生成
- **Playwright** → ブラウザーテスト
- **Morphllm** → 一括変換
- **Serena** → セッション永続化

</td>
<td width="50%">

### 🎯 **行動モード**
異なるコンテキスト用の**5つの適応モード**：
- **ブレインストーミング** → 適切な質問をする
- **オーケストレーション** → 効率的なツール調整
- **トークン効率** → 30-50%のコンテキスト節約
- **タスク管理** → システマチックな整理
- **内省** → メタ認知分析

</td>
</tr>
<tr>
<td width="50%">

### ⚡ **最適化されたパフォーマンス**
**より小さなフレームワーク、より大きなプロジェクト：**
- フレームワークフットプリントの削減
- コード用により多くのコンテキスト
- より長い会話が可能
- 複雑な操作を実現

</td>
<td width="50%">

### 📚 **ドキュメントの全面見直し**
開発者向けの**完全な書き直し**：
- 実際の例とユースケース
- 一般的な落とし穴を文書化
- 実用的なワークフローを含む
- より良いナビゲーション構造

</td>
</tr>
</table>

</div>

---

<div align="center">

## 📚 **ドキュメント**

### **SuperClaudeの完全ガイド**

<table>
<tr>
<th align="center">🚀 開始ガイド</th>
<th align="center">📖 ユーザーガイド</th>
<th align="center">🛠️ 開発者リソース</th>
<th align="center">📋 リファレンス</th>
</tr>
<tr>
<td valign="top">

- 📝 [**クイックスタートガイド**](Docs/Getting-Started/quick-start.md)  
  *素早く稼働開始*

- 💾 [**インストールガイド**](Docs/Getting-Started/installation.md)  
  *詳細な設定手順*

</td>
<td valign="top">

- 🎯 [**コマンドリファレンス**](Docs/User-Guide/commands.md)  
  *全21スラッシュコマンド*

- 🤖 [**エージェントガイド**](Docs/User-Guide/agents.md)  
  *14の専門エージェント*

- 🎨 [**行動モード**](Docs/User-Guide/modes.md)  
  *5つの適応モード*

- 🚩 [**フラグガイド**](Docs/User-Guide/flags.md)  
  *動作制御*

- 🔧 [**MCPサーバー**](Docs/User-Guide/mcp-servers.md)  
  *6つのサーバー統合*

- 💼 [**セッション管理**](Docs/User-Guide/session-management.md)  
  *状態の保存と復元*

</td>
<td valign="top">

- 🏗️ [**技術アーキテクチャ**](Docs/Developer-Guide/technical-architecture.md)  
  *システム設計詳細*

- 💻 [**コード貢献**](Docs/Developer-Guide/contributing-code.md)  
  *開発ワークフロー*

- 🧪 [**テストとデバッグ**](Docs/Developer-Guide/testing-debugging.md)  
  *品質保証*

</td>
<td valign="top">

- ✨ [**ベストプラクティス**](Docs/Reference/quick-start-practices.md)  
  *プロのコツとパターン*

- 📓 [**例のクックブック**](Docs/Reference/examples-cookbook.md)  
  *実世界のレシピ*

- 🔍 [**トラブルシューティング**](Docs/Reference/troubleshooting.md)  
  *一般的な問題と修正*

</td>
</tr>
</table>

</div>

---

<div align="center">

## 🤝 **貢献**

### **SuperClaudeコミュニティに参加**

あらゆる種類の貢献を歓迎します！参加方法は以下の通りです：

| 優先度 | 領域 | 説明 |
|:--------:|------|-------------|
| 📝 **高** | ドキュメンテーション | ガイドの改善、例の追加、誤字修正 |
| 🔧 **高** | MCP統合 | サーバー設定の追加、統合テスト |
| 🎯 **中** | ワークフロー | コマンドパターンとレシピの作成 |
| 🧪 **中** | テスト | テストの追加、機能の検証 |
| 🌐 **低** | 国際化 | ドキュメントの他言語翻訳 |

<p align="center">
  <a href="CONTRIBUTING.md">
    <img src="https://img.shields.io/badge/📖_読む-貢献ガイド-blue" alt="Contributing Guide">
  </a>
  <a href="https://github.com/SuperClaude-Org/SuperClaude_Framework/graphs/contributors">
    <img src="https://img.shields.io/badge/👥_表示-全貢献者-green" alt="Contributors">
  </a>
</p>

</div>

---

<div align="center">

## ⚖️ **ライセンス**

このプロジェクトは**MITライセンス**の下でライセンスされています - 詳細は[LICENSE](LICENSE)ファイルをご覧ください。

<p align="center">
  <img src="https://img.shields.io/badge/License-MIT-yellow.svg?" alt="MIT License">
</p>

</div>

---

<div align="center">

## ⭐ **Star履歴**

<a href="https://www.star-history.com/#SuperClaude-Org/SuperClaude_Framework&Timeline">
 <picture>
   <source media="(prefers-color-scheme: dark)" srcset="https://api.star-history.com/svg?repos=SuperClaude-Org/SuperClaude_Framework&type=Timeline&theme=dark" />
   <source media="(prefers-color-scheme: light)" srcset="https://api.star-history.com/svg?repos=SuperClaude-Org/SuperClaude_Framework&type=Timeline" />
   <img alt="Star History Chart" src="https://api.star-history.com/svg?repos=SuperClaude-Org/SuperClaude_Framework&type=Timeline" />
 </picture>
</a>


</div>

---

<div align="center">

### **🚀 SuperClaudeコミュニティによって情熱を込めて構築**

<p align="center">
  <sub>境界を押し広げる開発者のために❤️で作成</sub>
</p>

<p align="center">
  <a href="#-superclaude-フレームワーク">トップに戻る ↑</a>
</p>

</div>