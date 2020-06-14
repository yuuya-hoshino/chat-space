# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many : groups
- has_many : chats

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
### Association
- has_many : users
- has_many : chats
- has_many : groups_tags
- has_many  :tags, through: :groups_tags

## tagsテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many : groups_tags
- has_many : groups, through: :groups_tags

## groups_tagsテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|tag_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :tag

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
