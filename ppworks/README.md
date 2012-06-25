#【モクモクテーマ】モクモクすることを書く
* 木曜のHeroku meetup の資料ブラッシュアップ
* 水曜のrubyist tokyo meetupでの話ネタ考える
* 7/23のurl設計議論大会用のネタ考える

# もくもくの記録
今日できたこと、今日学んだ事、ハマったことなどの軸で記録


## 7/23のurl設計議論大会用のネタ考える

* indexに対して検索を書けるような場合はquery stringで良いか。
* 例えばフォローしているユーザー一覧
    * /follows
        * /follows?user_id=:user_id
    * /my/follows
    * /users/:user_id/follows
* 現在ログインしているユーザーに関連するresourceの定義
    * /my/user
    * /my/feed/posts
    * /my/follows
        * この場合新規リソースは/my/follows?
        * /followsのほうが良いのかも？ん？
        * backbone.js使うときとかGETとPOSTでurl変えるのがめんどくさそう。
* あるリソースの特定の絞込み
    * /reviews
    * /reviews/latest
    * /reviews?filter=latest
* pushStateのhistory.back()問題
    * /posts
    * /posts.json (jsライブラリ側でsuffix付ける)
    * /api/posts (scopeだけ切る)
