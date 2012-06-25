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
    * Varyを吐くといいかも http://sonic64.com/2004-02-06.html 


## 議論の結果

### フォローユーザーを表す
全体のresourcesが意味を成さないパターン

* /follows
    * own resources
    * GET
    * POST
    * DELETE

* /my/follows
    * own resources
    * GET
    * POST
    * DELETE

* /follows と /my/follows が同じ内容を返しても良い
* どっちでも良いのでは?

### 投稿内容を表す

* /posts
    * all resources
    * GET
    * POST
    * DELETE
* /my/posts
    * own resources
* /users/:user_id/posts
    * user's resources
* /my/follows/posts
    * my following's posts
* /posts/latest
    * latest posts
* /my/bookmarks/posts
    * my bookmarked posts

## ホワイトボードの図

![url 設計たたき台](https://github.com/sendagayarb/mokmok_2012-06-25/raw/master/ppworks/sendagaya_restful2012-06-25.jpg)











