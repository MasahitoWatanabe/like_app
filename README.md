# like_app
# 概要
ユーザーのログイン・メッセージの投稿・他のユーザーのメッセージに対するいいね
# 制作背景
ブログやツイッターのようなアプリを作成したことがあるが、ツイッターの機能にある他のユーザーの投稿に対するいいねを付けられる機能の仕組みが気になり実際に作ってみようと思った。
# DEMO
# 実装予定の内容
ユーザーのログイン・メッセージの投稿・他のユーザーのメッセージに対するいいね
# DB設計

------------------------------------
## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|

### Association

- has_many :posts, dependent: :destroy
- has_many :likes, dependent: :destroy
- has_many :liked_posts, through: :likes, source: :post

------------------------------------
## postsテーブル

|Column|Type|Options|
|------|----|-------|
|content|string|null: false|
|user_id|integer|null: false foreign_key: true|

### Association

- belongs_to :user
- has_many :likes
- has_many :liked_users, through: :likes, source: :user

------------------------------------
## likesテーブル

|Column|Type|Options|
|------|----|-------|
|post_id|integer|null: false foreign_key: true|
|user_id|integer|null: false foreign_key: true|

### Association

- belongs_to :user
- belongs_to :post

------------------------------------