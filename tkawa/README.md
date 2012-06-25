#【モクモクテーマ】モクモクすることを書く
* 7/23のURL設計勉強会用のネタ考える

# もくもくの記録
今日できたこと、今日学んだ事、ハマったことなどの軸で記録

## 7/23のURL設計勉強会用のネタ考える

> でも「そんなのどうでもいい」っていう人も多いと思うので、具体的なメリットと結びつけて語れればな、と思っています。とりあえずRailsに限っても、メリットはたくさんあるはず

> http://twitter.com/tkawa/status/217139844453896193

### はじめに

基本はリソースとCRUD。

画面は考えない。APIを設計する感覚に近い。

そのWebアプリで提供したいリソースは何か。

リソースに名前をつける。

Rails流では、collectionとmember（いわば拡張CRUD）。

```
           |  GET  |  POST  |  PUT   | DELETE  |
/users     | index | create |   -    |    -    |
/users/:id | show  |   -    | update | destroy |
```

collectionのリソース名は複数形。

もう1つのパターンは、singularリソース。

* グローバルに1つしかない
* memberリソースに対して has_one 関係
* sessionに対して has_one 関係

典型的なものは、「ログイン中のユーザー自身」を表すリソース。これはsessionに対して1つ。

ただし、なぜこのリソースが必要かをcredentialの面から考えること。

```
          |  GET  |  POST  |  PUT   | DELETE  |
/user     | show  | create | update | destroy |
```

singularリソースの名前は単数形。

#### 関連/子リソース

has_many や親リソースの一部(partial resource)は子リソースになりうる。

子リソースの名前は普通のリソースと同様。

関連 has_many の例

* /users/:id/articles
* /users/:user_id/articles/:id

同時に /articles も提供する場合、リソースが重複する。真に必要なのはどれか考えること。

#### partial resource の例

* /users/:id/name

特別に子リソースとして提供する必要があるかどうか考えること。

一般的には、partial updateを多用する場合には便利。（ただし汎用性があるので、自動化すべきかもしれない）


/ で区切った場合、必ず上にたどれないといけない。

followsとpostsの違い。
/user/


#### /username を使いたい。


### 参考文献
日本語の2冊。

* Webを支える技術
* RESTful Webサービス

英語の3冊。どれがいいかはあとで書く

* RESTful Web Services Cookbook
* REST API Design Rulebook
* REST in Practice
