# Pictweet DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|nickname|string|null: false|
### Association
- has_many :groups_users
- has_many :messeges
- has_many :groups,through:groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :groups_users
- has_many :comments
- has_many :users,through:groups_users
## messegesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|groups_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|index: true, null: false, unique: true|
|mail|string|null: false|
### Association
- has_many :groups,through:members
- has_many :messages
- has_many :users