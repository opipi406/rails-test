# Rails練習用
Ruby on Rails練習用リボジトリ


# Usage

## 1.srcフォルダを作成

## 2.Gemfileをsrcフォルダの中に移動

## 3.Docker上でRailsのプロジェクトを作成
```bash
docker-compose run web rails new . --force --database=mysql
```

## 4.リビルドしてコンテナを最新状態に更新
DockerfileやGemfileを修正した後はリビルドが必要
```bash
docker-compose build
```

## 5.データベースのconfig設定
src/config/database.yml  

以下に変更  
```bash
L17 password: password
L18 host: db
```

## 6.railsのコマンドでデータベースを作成
```bash
docker-compose run web rails db:create
```

## 7.railsの起動
```bash
docker-compose up
```
`localhost:3000` にアクセス

### バックグラウンドでコンテナ起動
```bash
docker-compose up -d
```

# Rails Note
## モデルの作成・削除
```bash
# モデルのみ作成
rails g model User
# モデルとマイグレーションファイルの作成
rails g model User name:string description:text age:integer
# モデルの削除
rails destroy model User
```
## コントローラーの作成
```bash
rails g controller users
```

## マイグレーションファイルの作成
```
rails g model User name:string description:text age:integer
```

## マイグレーション関連

### 基本操作
```bash
# マイグレーション実行
rails db:migrate
# マイグレーションの履歴・実行状態を表示
rails db:migrate:status
# シーディング実行
rails db:seed
```

### DBリセット
```bash
# ロールバック
rails db:rollback STEP={N}
# データベースリセット
rails db:reset
# すべてをやり直す
rails db:migrate:reset
```

### カラム追加
```bash
rails g migration add_column_to_users
```
```ruby
class AddColumnToUsers < ActiveRecord::Migration
  def change
    add_column :users, :mobile_phone, :string, after: :phone
  end
end
```

## View
### viewファイルだけを作成
```bash
rails g erb:scaffold User
```

## Railsコンソール
### コンソール実行
```bash
rails console
```

### レコードの作成・登録のテスト
```bash
user = User.new(name: "マキト", description: "hogehoge", age: 22)
user.save
```

# Docker Note
### railsのコンテナのbashを起動
```bash
docker-compose exec web /bin/bash
```

# Other
[docker-composeでRailsのGemを更新する時、docker buildするのを回避したい](https://qiita.com/neko-neko/items/abe912eba9c113fd527e)  
[【Rails6】Dockerコンテナを再起動しないとソースコードが反映されない](https://qiita.com/Kiyo_Karl2/items/147d604e625b8a55e12e)  
[【RubyonRails完全入門】開発の流れを超初心者向けに解説](https://www.sejuku.net/blog/96900)  
[render - Railsドキュメント](https://railsdoc.com/page/render)  
[railsでページ作成をする](https://qiita.com/you8/items/a7624fef49dedfdc71ae)
