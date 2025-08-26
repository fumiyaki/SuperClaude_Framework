<div align="center">

# 📦 SuperClaude インストールガイド

### **21個のコマンド、14個のエージェント、6個のMCPサーバーでClaude Codeを変革する**

<p align="center">
  <img src="https://img.shields.io/badge/version-4.0.8-blue?style=for-the-badge" alt="Version">
  <img src="https://img.shields.io/badge/Python-3.8+-green?style=for-the-badge" alt="Python">
  <img src="https://img.shields.io/badge/Platform-Linux%20|%20macOS%20|%20Windows-orange?style=for-the-badge" alt="Platform">
</p>

<p align="center">
  <a href="#-クイックインストール">クイックインストール</a> •
  <a href="#-要件">要件</a> •
  <a href="#-インストール方法">方法</a> •
  <a href="#-確認">確認</a> •
  <a href="#-トラブルシューティング">トラブルシューティング</a>
</p>

</div>

---

## ⚡ **クイックインストール**

<div align="center">

### **お好みの方法を選択**

| 方法 | コマンド | プラットフォーム | 最適な用途 |
|:------:|---------|:--------:|----------|
| **🐍 pipx** | `pipx install SuperClaude && SuperClaude install` | Linux/macOS | **✅ 推奨** - 分離された環境 |
| **📦 pip** | `pip install SuperClaude && SuperClaude install` | すべて | 従来のPythonセットアップ |
| **🌐 npm** | `npm install -g @bifrost_inc/superclaude && superclaude install` | すべて | Node.js開発者 |
| **🔧 開発** | `git clone ... && pip install -e ".[dev]"` | すべて | コントリビューター＆開発者 |

</div>

---

## 📋 **要件**

<div align="center">

<table>
<tr>
<td align="center" width="50%">

### ✅ **必須**

| コンポーネント | バージョン | 確認コマンド |
|-----------|---------|---------------|
| **Python** | 3.8+ | `python3 --version` |
| **pip** | 最新版 | `pip --version` |
| **Claude Code** | 最新版 | `claude --version` |
| **ディスク容量** | 50MB | `df -h` |

</td>
<td align="center" width="50%">

### 💡 **オプション**

| コンポーネント | 目的 | 確認コマンド |
|-----------|---------|---------------|
| **Node.js** | MCPサーバー | `node --version` |
| **Git** | バージョン管理 | `git --version` |
| **pipx** | 分離インストール | `pipx --version` |
| **RAM** | パフォーマンス | 1GB推奨 |

</td>
</tr>
</table>

</div>

<details>
<summary><b>🔍 クイックシステムチェック</b></summary>

```bash
# すべての要件を一度にチェック
python3 --version && echo "✅ Python OK" || echo "❌ Python missing"
claude --version && echo "✅ Claude Code OK" || echo "❌ Claude Code missing"
node --version 2>/dev/null && echo "✅ Node.js OK (optional)" || echo "⚠️ Node.js missing (optional)"
git --version 2>/dev/null && echo "✅ Git OK (optional)" || echo "⚠️ Git missing (optional)"
```

</details>

---

## 🚀 **インストール方法**

<div align="center">

### **詳細なインストール手順**

</div>

### **方法1: pipx（推奨）**

<table>
<tr>
<td width="60%">

```bash
# pipxがない場合はインストール
python3 -m pip install --user pipx
python3 -m pipx ensurepath

# SuperClaudeをインストール
pipx install SuperClaude

# インストーラーを実行
SuperClaude install
```

</td>
<td width="40%">

**✅ 利点:**
- 分離された環境
- 依存関係の競合なし
- クリーンなアンインストール
- 自動PATH設定

**📍 最適な用途:**
- Linux/macOSユーザー
- クリーンシステムインストール
- 複数のPythonプロジェクト

</td>
</tr>
</table>

### **方法2: pip（従来型）**

<table>
<tr>
<td width="60%">

```bash
# 標準インストール
pip install SuperClaude

# またはユーザーインストール
pip install --user SuperClaude

# インストーラーを実行
SuperClaude install
```

</td>
<td width="40%">

**✅ 利点:**
- どこでも動作
- Pythonユーザーに馴染み深い
- 直接インストール

**📍 最適な用途:**
- Windowsユーザー
- 仮想環境
- クイックセットアップ

</td>
</tr>
</table>

### **方法3: npm（クロスプラットフォーム）**

<table>
<tr>
<td width="60%">

```bash
# グローバルインストール
npm install -g @bifrost_inc/superclaude

# インストーラーを実行
superclaude install
```

</td>
<td width="40%">

**✅ 利点:**
- クロスプラットフォーム
- NPMエコシステム
- JavaScriptに馴染み深い

**📍 最適な用途:**
- Node.js開発者
- NPMユーザー
- クロスプラットフォームニーズ

</td>
</tr>
</table>

### **方法4: 開発用インストール**

<table>
<tr>
<td width="60%">

```bash
# リポジトリをクローン
git clone https://github.com/SuperClaude-Org/SuperClaude_Framework.git
cd SuperClaude_Framework

# 開発モードでインストール
pip install -e ".[dev]"

# インストールをテスト
SuperClaude install --dry-run
```

</td>
<td width="40%">

**✅ 利点:**
- 最新機能
- プロジェクトに貢献可能
- 完全なソースアクセス

**📍 最適な用途:**
- コントリビューター
- カスタマイズ
- 新機能のテスト

</td>
</tr>
</table>

---

## 🎛️ **インストールオプション**

<div align="center">

### **インストールをカスタマイズ**

| オプション | コマンド | 説明 |
|--------|---------|-------------|
| **インタラクティブ** | `SuperClaude install` | プロンプトによるガイド付きセットアップ |
| **特定コンポーネント** | `SuperClaude install --components core mcp modes` | 必要なもののみインストール |
| **プレビューモード** | `SuperClaude install --dry-run` | インストール予定を確認 |
| **強制インストール** | `SuperClaude install --force --yes` | すべての確認をスキップ |
| **コンポーネント一覧** | `SuperClaude install --list-components` | 利用可能なコンポーネントを表示 |

</div>

---

## ✅ **確認**

<div align="center">

### **インストールの成功を確認**

</div>

### **ステップ1: インストールを確認**

```bash
# SuperClaudeのバージョンを確認
python3 -m SuperClaude --version
# 期待される結果: SuperClaude 4.0.8

# インストールされたコンポーネントを一覧表示
SuperClaude install --list-components
# 期待される結果: 利用可能なコンポーネントの一覧
```

### **ステップ2: Claude Codeでテスト**

```bash
# Claude Codeを開いて以下のコマンドを試してください:
/sc:brainstorm "test project"     # 発見的質問が起動するはず
/sc:analyze README.md              # 構造化分析を提供するはず
@agent-security "review code"     # セキュリティ専門家が起動するはず
```

### **ステップ3: インストール内容**

<div align="center">

| 場所 | 内容 | サイズ |
|----------|----------|------|
| `~/.claude/` | フレームワークファイル | ~50MB |
| `~/.claude/CLAUDE.md` | メインエントリーポイント | ~2KB |
| `~/.claude/*.md` | 動作指示 | ~200KB |
| `~/.claude/claude-code-settings.json` | MCP設定 | ~5KB |

</div>

---

## 🛠️ **管理**

<div align="center">

<table>
<tr>
<th>📦 更新</th>
<th>💾 バックアップ</th>
<th>🗑️ アンインストール</th>
</tr>
<tr>
<td>

```bash
# 最新版に更新
pip install --upgrade SuperClaude
SuperClaude update
```

</td>
<td>

```bash
# バックアップを作成
SuperClaude backup --create

# バックアップを復元
SuperClaude backup --restore [file]
```

</td>
<td>

```bash
# フレームワークを削除
SuperClaude uninstall

# パッケージをアンインストール
pip uninstall SuperClaude
```

</td>
</tr>
</table>

</div>

---

## 🔧 **トラブルシューティング**

<details>
<summary><b>❌ PEP 668エラー（Pythonパッケージ管理）</b></summary>

このエラーは外部管理されたPython環境を持つシステムで発生します。

**解決策（推奨順）:**

```bash
# オプション1: pipxを使用（推奨）
pipx install SuperClaude

# オプション2: ユーザーインストール
pip install --user SuperClaude

# オプション3: 仮想環境
python3 -m venv superclaude-env
source superclaude-env/bin/activate  # Linux/macOS
# または
superclaude-env\Scripts\activate  # Windows
pip install SuperClaude

# オプション4: 強制（注意して使用）
pip install --break-system-packages SuperClaude
```

</details>

<details>
<summary><b>❌ コマンドが見つからない</b></summary>

インストール後に`SuperClaude`コマンドが見つからない場合:

```bash
# パッケージがインストールされているか確認
python3 -m pip show SuperClaude

# Pythonモジュールとして実行
python3 -m SuperClaude install

# PATHに追加（--userを使用した場合）
export PATH="$HOME/.local/bin:$PATH"
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc  # Linux
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc   # macOS
```

</details>

<details>
<summary><b>❌ Claude Codeが見つからない</b></summary>

Claude CodeがインストールされていないかPATHにない場合:

1. [https://claude.ai/code](https://claude.ai/code)からダウンロード
2. プラットフォーム指示に従ってインストール
3. `claude --version`で確認
4. インストール後にターミナルを再起動

</details>

<details>
<summary><b>❌ 権限拒否</b></summary>

インストール中の権限エラーの場合:

```bash
# ユーザーインストールを使用
pip install --user SuperClaude

# またはsudoを使用（非推奨）
sudo pip install SuperClaude

# より良い方法: pipxを使用
pipx install SuperClaude
```

</details>

<details>
<summary><b>❌ Pythonまたはpipがない</b></summary>

**Linux（Ubuntu/Debian）:**
```bash
sudo apt update
sudo apt install python3 python3-pip python3-venv
```

**macOS:**
```bash
# 必要に応じてHomebrewを最初にインストール
brew install python3
```

**Windows:**
- [python.org](https://python.org)からダウンロード
- インストール時に「PythonをPATHに追加」をチェック
- インストール後にターミナルを再起動

</details>

---

## 📚 **次のステップ**

<div align="center">

### **あなたの学習ジャーニー**

<table>
<tr>
<th>🌱 ここから始める</th>
<th>🌿 スキルを拡張</th>
<th>🌲 フレームワークをマスター</th>
</tr>
<tr>
<td valign="top">

**最初の週:**
- [クイックスタートガイド](quick-start.md)
- [コマンドリファレンス](../User-Guide/commands.md)
- `/sc:brainstorm`を試す

</td>
<td valign="top">

**2-3週目:**
- [動作モード](../User-Guide/modes.md)
- [エージェントガイド](../User-Guide/agents.md)
- [例のクックブック](../Reference/examples-cookbook.md)

</td>
<td valign="top">

**上級:**
- [MCPサーバー](../User-Guide/mcp-servers.md)
- [技術アーキテクチャ](../Developer-Guide/technical-architecture.md)
- [コード貢献](../Developer-Guide/contributing-code.md)

</td>
</tr>
</table>

</div>

---

<div align="center">

### **🎉 インストール完了！**

以下が利用可能になりました:

<p align="center">
  <b>21個のコマンド</b> • <b>14個のAIエージェント</b> • <b>6個の動作モード</b> • <b>6個のMCPサーバー</b>
</p>

**始める準備はできましたか？** Claude Codeで`/sc:brainstorm`を試して、初のSuperClaude体験をしてみましょう！

<p align="center">
  <a href="quick-start.md">
    <img src="https://img.shields.io/badge/📖_続きを読む-クイックスタートガイド-blue?style=for-the-badge" alt="Quick Start">
  </a>
</p>

</div>