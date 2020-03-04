# chat-space DB設計

## users テーブル

|Column|Type|Options|
|------|----|-------|
|nickname|string|index: true, null: false, unique: true|
|email|string|null: false|
|password|string|null: false|

## Association
- has_many :messages
- has_many :groups_users
- has_many :groups, through :groups_users

## groupsテーブル

|Column|Type|Option|
|------|----|------|
|name|string|null: false|

## Association
- has_many :messages
- has_many :users
- has_many :users, through :groups_users


## messagesテーブル

|Column|Type|Option|
|------|----|------|
|text|text||
|image|text||

## Association
belongs_to :user


## groups_usersテーブル

|Column|Type|Options|
|------|----|-------|
|user|references|null: false, foreign_key: true|
|group|references|null: false, foreign_key: true|

### Association
- belongs_to :group
- belongs_to :user
