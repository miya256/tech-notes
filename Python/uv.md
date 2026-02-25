## 概要
Rust でつくられた、Python環境を構築できるツール
pip, venvなどをまとめたもの

## 使い方

### uv をインストール
- すでに入っているか確認
```
uv --version
```
- 入っていないなら
```
pip install uv
```

### uv init
- リポジトリのルートで以下を実行。 `.python-version` と `pyproject.toml` と `main.py` がつくられる。
- `main.py` はいらないので消しちゃおう。
```
uv init
```

### uv sync
- init したらとりあえずこれをしよう。 `.venv` と `uv.lock` がつくられる。
```
uv sync
```

### ライブラリの追加
- `pyproject.toml` と `uv.lock` が自動で更新されます。
- 依存ライブラリも勝手に入ります。
- `.venv/Lib/site-packages` の中に追加されます。
- `requirements.txt` がある場合はこれで一括でできます。
```
uv add -r requirements.txt
```
- 一つずつやる場合は、
```
uv add <library>
```

### 実行
- コマンドの先頭に `uv run` を付けよう。
```
uv run python main.py
```