# README

# chat space DB設計

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|email|string|null: false|
|password|string|null: false|
|username|string|null: false|
|group_id|integer|null: false, foreign_key: true|
### Association
- has_many :chats
- has_many :user_group
- has_many  :groups,  through:  :user_group

## chatsテーブル
|Column|Type|Options|
|------|----|-------|
|body|text|null: false|
|image|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group


## groupテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :user_group
- has_many  :users,  through:  :user_group
- has_many :chats

## user_groupテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group
