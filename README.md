# テーブル設計

## users テーブル

| Column             | Type   | Options                  |
| ------------------ | ------ | ------------------------ |
| nickname           | string | null: false              |
| email              | string | null: false unique: true |
| encrypted_password | string | null: false              |

### Association

- has_one :like
- has_many :comments

## likes テーブル

| Column   | Type       | Options                        |
| -------- | ---------- | ------------------------------ |
| like_id  | integer    | null: false                    |
| hour_id  | integer    | null: false                    |
| cost_id  | integer    | null: false                    |
| user     | references | null: false, foreign_key: true |

### Association

- has_many :comments
- belongs_to :user

## comments テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | string     |                                |
| user    | references | null: false, foreign_key: true |
| like    | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :like