## 概要
GitHubで自動で型チェックとかをする

## 方法
## ci.yml作成
- リポジトリのルートに、 `.github/workflows/ci.yml` を作成

### 中身を書こう
例 (インデントは2が一般的らしい)
```yml
name: Type Check # ワークフローの名前（GitHubの画面に表示されるラベル）

on: # いつ起動するか
  pull_request:
  
jobs: # 実行する作業一覧（並列に実行される）
  typecheck: # 作業名
    runs-on: ubuntu-latest # どの環境でやるか
    
    steps: # 手順
	  # リポジトリのコードをCI環境にコピー
      - uses: actions/checkout@v4
      
      # uv を CI環境にインストール
      # GitHubサーバは毎回クリーンだから、毎回インストール必要
      - name: Install uv
        run: curl -LsSf https://astral.sh/uv/install.sh | sh
      
      # 依存を入れる
      - name: Sync
        run: uv sync
      
      # 型チェックを実行
      # これもインストール必要だがuvに入れとけば、uv syncのときに入るはず
      - name: Run pyright
        run: uv run pyright
```

## ログ
- ログが長いときは、ファイルに出力するとよい
```
uv run oj-verify run 2>&1 | tee result.log | grep -E "INFO:onlinejudge_verify.verify:|\[SUCCESS\]"
```

### `2>&1`
- 標準出力の番号は1、標準エラーの番号は2である。
- 普通にファイルに書き込む場合、標準出力だけ書き込まれ、エラーは画面に出る。
- ここでこれ、 **2は1と同じ場所に流せ** という意味。これでエラーもファイルに書かれる。

### `tee`
- ファイルに書き込みながら、画面にも出力する

### `grep`
- 指定した部分文字列の含まれる行だけ取り出すやつ
- `-i` は大文字小文字を区別しない
- `-E` orを使いたい場合

[[pyright]]