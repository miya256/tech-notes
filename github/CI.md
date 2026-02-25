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
  
jobs: # 実行する作業一覧
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

[[pyright]]