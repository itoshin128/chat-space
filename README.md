# ChatSpace

## users table
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|email|string|null: false, unique: true|
### Association
- has_many :messages
- has_many :group_users
- has_many :groups, through: :groups_users

## messages table
|Column|Type|Options|
|------|----|-------|
|body|text||
|image|string||
|group_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

## groups table
|Column|Type|Options|
|------|----|-------|
|group_name|text|null: false, unique: true|
### Association
- has_many :messages
- has_many :group_users
- has_many :users through::groups_users

## groups_users table
|Column|Type|Options|
|------|----|-------|
|post_id|integer|null: false, foreign_key: true|
|tag_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user