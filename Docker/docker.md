dockerはゲーム機で、コンテナはその中のゲームソフトみたいな感じ

command not foundのときは、ドッカーを開いて、右上のSetting、左のResourceタブの、WSL integrationタブでrefech

## command
### 起動中のコンテナ確認
```
docker ps
```
### バックグラウンドで起動
```
docker compose up -d
```
### 停止
```
docker compose down
```
### ポートを確認できる？
```
docker compose ps
```
### 全コンテナ削除
```
docker rm -f $(docker ps -aq)
```
### 全イメージ削除
```
docker rmi -f $(docker images -aq)
```