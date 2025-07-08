# インストール方法

インストール方法は 2 つ提供しています。方法 2（uv を使用）は、より高速なインストールと優れた依存関係管理のため推奨されています。

## 方法 1：conda を使用

1. 新しい conda 環境を作成します：

```bash
conda create -n open_manus python=3.12
conda activate open_manus
```

2. リポジトリをクローンします：

```bash
git clone https://github.com/xpack-ai/OpenManus.git
cd OpenManus
```

3. 依存関係をインストールします：

```bash
pip install -r requirements.txt
```

## 方法 2：uv を使用（推奨）

1. uv（高速な Python パッケージインストーラーと管理機能）をインストールします：

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

2. リポジトリをクローンします：

```bash
git clone https://github.com/xpack-ai/OpenManus.git
cd OpenManus
```

3. 新しい仮想環境を作成してアクティベートします：

```bash
uv venv --python 3.12
source .venv/bin/activate  # Unix/macOSの場合
# Windowsの場合：
# .venv\Scripts\activate
```

4. 依存関係をインストールします：

```bash
uv pip install -r requirements.txt
```

## ブラウザ自動化ツール（オプション）

```bash
playwright install
```

# 設定

OpenManus を使用するには、LLM API の設定が必要です。以下の手順に従って設定してください：

1. `config`ディレクトリに`config.toml`ファイルを作成します（サンプルからコピーできます）：

```bash
cp config/config.example.toml config/config.toml
```

2. `config/config.toml`を編集して API キーを追加し、設定をカスタマイズします：

```toml
# グローバルLLM設定
[llm]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # 実際のAPIキーに置き換えてください
max_tokens = 4096
temperature = 0.0

# 特定のLLMモデル用のオプション設定
[llm.vision]
model = "gpt-4o"
base_url = "https://api.openai.com/v1"
api_key = "sk-..."  # 実際のAPIキーに置き換えてください
```
