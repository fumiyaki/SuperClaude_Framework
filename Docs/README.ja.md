# SuperClaude ドキュメント

## 🎯 重要な理解

**SuperClaudeはClaude Codeのためのコンテキストフレームワークです** - Claude Codeが読み込んで能力を強化する行動指示ファイルをインストールします。

### 仕組み
1. **インストール**: Python CLIがコンテキストファイルを`~/.claude/`にインストール
2. **コマンド**: `/sc:analyze`と入力 → Claude Codeが`analyze.md`指示ファイルを読み込み
3. **動作**: Claudeがコンテキストファイルで定義された行動を採用
4. **結果**: コンテキスト切り替えによる強化された開発ワークフロー

## 🚀 クイックスタート（5分）

**新規ユーザー**: [クイックスタートガイド →](Getting-Started/quick-start.md)
```bash
# Linux/macOS推奨
pipx install SuperClaude && SuperClaude install

# 従来の方法
pip install SuperClaude && SuperClaude install

# Claude Codeで試してください: /sc:brainstorm "Webアプリアイデア"
```

**問題がある場合**: [クイック修正 →](Reference/common-issues.md) | [トラブルシューティング →](Reference/troubleshooting.md)

## 📚 ドキュメント構造

### 🌱 ここから始める（新規ユーザー）
| ガイド | 目的 |
|-------|---------|
| **[クイックスタート](Getting-Started/quick-start.md)** | セットアップと最初のコマンド |
| **[インストール](Getting-Started/installation.md)** | 詳細セットアップ指示 |
| **[コマンドガイド](User-Guide/commands.md)** | 全21個の`/sc:`コマンド |

### 🌿 日常使用（通常ユーザー）
| ガイド | 目的 | 用途 |
|-------|---------|---------|
| **[コマンドガイド](User-Guide/commands.md)** | 全`/sc:`コマンドをマスター | 日常開発 |
| **[エージェントガイド](User-Guide/agents.md)** | 14個のドメイン専門家（`@agent-*`） | エキスパート支援 |
| **[フラグガイド](User-Guide/flags.md)** | コマンド動作修正 | 最適化 |
| **[モードガイド](User-Guide/modes.md)** | 5個の動作モード | ワークフロー最適化 |

### 🌲 リファレンス＆上級（パワーユーザー）
| ガイド | 目的 | 用途 |
|-------|---------|---------|
| **[トラブルシューティング](Reference/troubleshooting.md)** | 問題解決 | 問題発生時 |
| **[例のクックブック](Reference/examples-cookbook.md)** | 実用使用パターン | ワークフロー学習 |
| **[MCPサーバー](User-Guide/mcp-servers.md)** | 6個の強化機能 | 高度機能 |

### 🔧 開発＆貢献
| ガイド | 目的 | 対象読者 |
|-------|---------|----------|
| **[技術アーキテクチャ](Developer-Guide/technical-architecture.md)** | システム設計 | 貢献者 |
| **[貢献](Developer-Guide/contributing-code.md)** | 開発ワークフロー | 開発者 |

## 🔑 主要概念

### インストールされるもの
- **Python CLIツール** - フレームワークインストールを管理
- **コンテキストファイル** - `~/.claude/`内の`.md`行動指示
- **MCP設定** - オプションの外部ツール設定

### フレームワークコンポーネント
- **21個のコマンド**（`/sc:*`） - ワークフロー自動化パターン
- **14個のエージェント**（`@agent-*`） - ドメイン専門家
- **5個のモード** - 動作修正パターン
- **6個のMCPサーバー** - オプションの外部ツール

## 🚀 クイックコマンドリファレンス

### ターミナルで（インストール）
```bash
# フレームワークインストール（いずれか一つを選択）
pipx install SuperClaude       # Linux/macOS推奨
pip install SuperClaude        # 従来の方法
npm install -g @bifrost_inc/superclaude  # クロスプラットフォーム

# 設定と保守
SuperClaude install            # Claude Codeを設定
SuperClaude update             # フレームワークを更新
python3 -m SuperClaude --version  # インストールを確認
```

### Claude Codeで（使用）
```bash
/sc:brainstorm "プロジェクトアイデア"              # 新しいプロジェクトを開始
/sc:implement "機能"                    # 機能を構築
/sc:analyze src/                           # コードを分析
@agent-python-expert "これを最適化"      # 手動専門家
@agent-security "認証をレビュー"   # セキュリティレビュー
```

## 📊 フレームワーク vs ソフトウェア比較

| コンポーネント | タイプ | 実行場所 | 機能 |
|-----------|------|---------------|--------------|
| **SuperClaudeフレームワーク** | コンテキストファイル | Claude Codeが読み込み | AI動作を修正 |
| **Claude Code** | ソフトウェア | あなたのコンピュータ | すべてを実行 |
| **MCPサーバー** | ソフトウェア | Node.jsプロセス | ツールを提供 |
| **Python CLI** | ソフトウェア | Pythonランタイム | インストールを管理 |

## 🔄 すべてのつながり

```
ユーザー入力 → Claude Code → SuperClaudeコンテキストを読み込み → 修正された動作 → 強化された出力
                ↓
        MCPサーバーを使用
         （設定されている場合）
```

## 🆘 ヘルプを得る

**クイック問題**（< 2分）: [一般的な問題 →](Reference/common-issues.md)  
**複雑な問題**: [完全トラブルシューティングガイド →](Reference/troubleshooting.md)  
**インストール問題**: [インストールガイド →](Getting-Started/installation.md)  
**コマンドヘルプ**: [コマンドガイド →](User-Guide/commands.md)  
**コミュニティサポート**: [GitHub Discussions](https://github.com/SuperClaude-Org/SuperClaude_Framework/discussions)

## 🤔 一般的な誤解の明確化

❌ **「SuperClaudeはAIアシスタントです」**  
✅ SuperClaudeはClaude Codeを強化する設定フレームワークです

❌ **「SuperClaudeを実行しています」**  
✅ SuperClaudeコンテキストが読み込まれたClaude Codeを実行しています

❌ **「Claude Codeが実行；SuperClaudeが私のコマンドにコンテキストを提供」**  
✅ Claude Codeがすべてを実行；SuperClaudeが指示を提供

❌ **「.mdファイルはドキュメントです」**  
✅ .mdファイルがフレームワークです - アクティブな指示セット

---

*覚えておくこと: SuperClaudeはコンテキストを通じてClaude Codeを強化します - それを置き換えたり並行して実行したりしません。すべてがClaude Code自体内で発生します。*