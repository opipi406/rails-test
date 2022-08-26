# Rails練習用
Ruby on Rails練習用リボジトリ


# Usage

## 1.srcフォルダを作成

## 2.Gemfileをsrcフォルダの中に移動

## 3.Docker上でRailsのプロジェクトを作成
```
docker-compose run rails new . --force --database=mysql
```

## 4.リビルドしてコンテナを最新状態に更新
DockerfileやGemfileを修正した後はリビルドが必要
```
docker-compose build
```

## 5.データベースのconfig設定
src/config/database.yml  

以下に変更  
```
L17 password: password
L18 host: db
```

## 6.railsのコマンドでデータベースを作成
```
docker-compose run web rails db:create
```

## 7.railsの起動
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

# Other
[docker-composeでRailsのGemを更新する時、docker buildするのを回避したい](https://qiita.com/neko-neko/items/abe912eba9c113fd527e)
