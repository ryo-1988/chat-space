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
## messagesテーブル

|Column|Type|Notnull|Option|index|
|------|----|-------|------|-----|
|body|text|YES|
|image|string|YES|
|group_id|references|YES|foreign_key: true|YES|
|user_id|references|YES|foreign_key: true|YES|

### Association
- belongs_to :user
- belongs_to :group

## usersテーブル

|Column|Type|Notnull|Options|index|
|------|----|-------|-------|-----|
|name|string|YES|null: false, unique: true|YES|

###Association
- has_many :messages
- has_many :group_members
- has_many :groups, through: :group_members

## groupsテーブル

|Columns|Type|Notnull|Options|index|
|-------|----|-------|-------|-----|
|name|string|YES|null: false|

###Association
- has_many :messages
- has_many :group_members
- has_many :users, through: :group_members

## group_membersテーブル

|Columns|Type|Notnull|Options|index|
|-------|----|-------|-------|-----|
|group_id|references|YES|foreign_key: true|YES|
|user_id|references|YES|foreign_key: true|YEs|

### Associaion
- belongs_to :user
- belongs_to :group