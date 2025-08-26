# SuperClaude PyPI 公開スクリプト

このディレクトリには、SuperClaude を PyPI にビルドおよび公開するためのスクリプトが含まれています。

## スクリプト

### `publish.sh` - メイン公開スクリプト
一般的な公開タスク用の使いやすいシェルスクリプト：

```bash
# TestPyPI へのテストアップロード
./scripts/publish.sh test

# TestPyPI からのテストインストール
./scripts/publish.sh test-install

# PyPI への本番アップロード
./scripts/publish.sh prod

# パッケージのビルドのみ
./scripts/publish.sh build

# ビルド成果物のクリーンアップ
./scripts/publish.sh clean

# プロジェクト構造の検証
./scripts/publish.sh check
```

### `build_and_upload.py` - 高度なビルドスクリプト
ビルドとアップロードプロセスを詳細に制御できるPythonスクリプト：

```bash
# TestPyPI へビルドしてアップロード
python scripts/build_and_upload.py --testpypi

# TestPyPI からテストインストール
python scripts/build_and_upload.py --testpypi --test-install

# 本番アップロード（確認付き）
python scripts/build_and_upload.py

# 検証をスキップ（高速ビルド用）
python scripts/build_and_upload.py --skip-validation --testpypi

# クリーンアップのみ
python scripts/build_and_upload.py --clean
```

## 前提条件

1. **PyPI アカウント**: https://pypi.org/account/register/ で登録
2. **API トークン**: https://pypi.org/manage/account/ でトークンを生成
3. **設定**: `~/.pypirc` を作成：
   ```ini
   [pypi]
   username = __token__
   password = pypi-[your-production-token]
   
   [testpypi]
   repository = https://test.pypi.org/legacy/
   username = __token__
   password = pypi-[your-test-token]
   ```

## GitHub Actions

`.github/workflows/publish-pypi.yml` ワークフローが公開を自動化します：

- **自動**: GitHub リリースが作成されたときに PyPI に公開
- **手動**: TestPyPI アップロード用に手動でトリガー可能
- **検証**: パッケージの検証とインストールテストを含む

### 必要なシークレット

GitHub リポジトリの設定 → Secrets and variables → Actions で設定：

- `PYPI_API_TOKEN`: 本番 PyPI トークン
- `TEST_PYPI_API_TOKEN`: TestPyPI トークン

## 公開ワークフロー

### 1. 開発リリース (TestPyPI)
```bash
# ビルドとアップロードプロセスのテスト
./scripts/publish.sh test

# パッケージが正しくインストールされることを確認
./scripts/publish.sh test-install
```

### 2. 本番リリース (PyPI)

#### オプション A: 手動
```bash
# 直接アップロード（確認が必要）
./scripts/publish.sh prod
```

#### オプション B: GitHub リリース（推奨）
1. コード内のバージョンを更新
2. 変更をコミットしてプッシュ
3. GitHub で新しいリリースを作成
4. GitHub Actions が自動的にビルドして公開

## バージョン管理

公開前に、以下のファイル間でバージョンの一貫性を確認：
- `pyproject.toml`
- `SuperClaude/__init__.py`
- `SuperClaude/__main__.py`
- `setup/__init__.py`

ビルドスクリプトは自動的にバージョンの一貫性を検証します。

## トラブルシューティング

### ビルドエラー
- Python バージョンの互換性を確認（≥3.8）
- 必要なファイルがすべて存在することを確認
- `pyproject.toml` の構文を検証

### アップロードエラー
- API トークンが正しいことを確認
- PyPI に既にバージョンが存在しないか確認
- パッケージ名が利用可能であることを確認

### インポートエラー
- パッケージ構造を確認（`__init__.py` ファイル）
- すべての依存関係がリストされていることを確認
- 最初にローカルインストールをテスト

## セキュリティに関する注意事項

- API トークンを絶対にバージョン管理にコミットしない
- 認証情報には環境変数または `.pypirc` を使用
- トークンには最小限必要な権限のみを付与
- GitHub Actions には Trusted Publishing の使用を検討