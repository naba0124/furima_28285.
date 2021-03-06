# テーブル設計

## users テーブル

| Column                    | Type   | Options     |
| --------                  | ------ | ----------- |
| nickname                  | string | null: false |
| email                     | string | null: false |
| password                  | string | null: false |
| passwoed_confirmation     | string | null: false |
| bithday                   | date   | null: false |
| firstname                 | string | null: false |
| lastname                  | string | null: false |
| firstname_kana            | string | null: false |
| lastname_kana             | string | null: false |

### Association

- has_many :comments
- has_many :items
- has_one :transactions

## comments テーブル

| Column | Type   | Options     |
| ------ | ------ | ----------- |
| user_id| integer| null: false |
| comments| text  | null: false |

### Association

- belongs_to :users
- belongs_to :items

## items テーブル

| Column | Type       | Options                    |
| ------ | ---------- | -------------------------- |
| name   | integer    |   null: false              |
| image  | text       | null: false                |
| categoly| integer   | null: false                |
| price  | integer    | null: false                |
| user_id| integer    | null: false, foreign_key: true |
| text   | text        | null: false               |
| stetus | intger      | null: false               |
| address_origin| integer | null: false             |
| burden | integer     | null: false               |
| delivery_time| integer | null: false             |

### Association

- has_many :comments
- belongs_to :users
- has_one :transaction





## address テーブル

| Column  | Type       | Options    |
| ------- | ---------- | ---------- |
| post_number | string | null: false|
| prefectures| integer | null: false|
| city    | string     | null: false |
| address | string     | null: false |
| build_name| string   |             |
|transaction| integer  |null:false, foreign_key:true|
| tel     | string     | null: false |

### Association
- belongs_to :transaction

## transactions テーブル

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| user_id | integer    |  null:false, foreign_key:true  |
| item_id | integer    |  null:false, foreign_key:true  |

### Association
- has_one :address
- belongs_to :users
- belongs_to :items
