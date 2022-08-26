# Rails練習用
Ruby on Rails練習用リボジトリ


# Usage

## 1.Docker上でRailsのプロジェクトを作成
```
docker-compose run rails new . --database-mysql
```

## 2.リビルドしてコンテナを最新状態に更新
DockerfileやGemfileを修正した後はリビルドが必要
```
docker-compose build
```

## 3.データベースのconfig設定
src/config/database.yml  

以下に変更  
```
L17 password: password
L18 host: db
```

## 4.railsのコマンドでデータベースを作成
docker-compose run web rails db:create

---

初期設定完了!!

---

## 5.railsの起動
```
docker-compose up
```
`localhost:3000` にアクセス

### バックグラウンドでコンテナ起動
```
docker-compose up -d
```

# Note

### railsのコンテナのbashを起動
```
docker-compose exec web /bin/bash
```