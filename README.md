## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many : groups , through: :groups_users
- has_many : chats
- has_many : groups_users

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many : users , through: :groups_users
- has_many : chats
- has_many : groups_users

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|group|references|null: false, foreign_key: true|
|user|references|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## chatsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text||
|image|string||
|user|references|null: false,foreign_key: true|
|group|references|null: false,foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
