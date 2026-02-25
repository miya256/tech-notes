## 概要
型チェックツール

## インストール方法
```
pip install pyright
```

- uv に入れる場合
- `--dev` は、uv の オプション。開発用ですよーという意味。
```
uv add --dev pyright
```

## 設定
uv で使ったので、それだけ説明する

### チェックをしたいファイルを指定
- `pyproject.toml` に以下を書く
```
[tool.pyright]
include = ["test/auto_test"]
```

## 実行
```
pyright
```

[[uv]]