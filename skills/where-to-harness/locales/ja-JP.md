# Locale pack: Japan (ja-JP)

Search terms for trips **in Japan**, whatever language the person speaks. Each row matches an entry in the core dictionary (`../dictionary.md`) by its "Core entry" name. When the person doesn't read Japanese, show each term with a short gloss.

日本国内の旅行で使う検索語・除外語。コア辞書の項目に「Core entry」の名前で対応する。

- **検索語・除外語**: `-語` は除外、`"…"` は完全一致
- **日本での条件**: コア辞書の「When it applies」に足す、日本ならではの事情。無ければ「—」

## Local sites

Booking, gourmet and review sites in Japan. **Never auto-fetch their pages.** Use them only in `site:` for search links the person opens themselves.

| Site | Domain | What people check there |
|---|---|---|
| 食べログ (Tabelog) | `tabelog.com` | Restaurant reviews, seating, private rooms |
| ホットペッパーグルメ | `hotpepper.jp` | Restaurant courses, seating, reservations |
| 一休.com | `ikyu.com` | Hotel and ryokan prices, plans |
| じゃらん | `jalan.net` | Hotel and ryokan prices, availability, reviews |
| 楽天トラベル | `travel.rakuten.co.jp` | Hotel and ryokan prices, availability, reviews |

## Terms

| Core entry | 暗黙知 | 検索語・除外語 | 日本での条件 |
|---|---|---|---|
| Probably noisy / want to eat in peace | うるさそう／落ち着いて食べたい | `カウンター` `小上がり` `-宴会` `-飲み放題` `-団体` | 年末（忘年会）・週末に強く効く |
| Avoid chains | チェーンは避けたい | 有名チェーン名を `-` で並べる（例 `-鳥貴族` `-磯丸水産` `-魚民` `-白木屋` `-笑笑` `-金の蔵` `-ミライザカ` `-はなの舞` `-塚田農場` `-串カツ田中`。例であって全部ではない） | 飲食グループ（同じ会社が別の店名・業態で出す店）はチェーンとしない。同じ店名が数店だけなら「未確認」で残し、本人に任せる |
| Must be open when we go | 行く時間に開いていてほしい | `営業時間` `定休日` `日曜営業` `ラストオーダー` `当日予約` | 日曜・祝日休みの店、年末年始休業が多い。L.O. は閉店の30〜60分前が多い |
| Want a local feel | 地元感がほしい | `郷土料理` `地物` `地酒` `-チェーン` | — |
| Food that looks carefully made | 料理が丁寧そう | `"料理長"` `釜飯` `コース` | — |
| Can't tell the quality of the ingredients | 食材の質が読めない | `"タグ付き"` `ブランド名` `活` | カニなど季節の食材 |
| Avoid raw food (health or taste) | 生ものを避けたい（体調・好み） | `加熱` `焼き` `炙り` `煮付け` | — |
| Get bored eating the same kind of food | 同じ系統の料理が続くと飽きる | `素泊まり` `朝食のみ` | — |
| Good location / want to walk around a bit | 立地が良い／少し歩いて楽しみたい | `徒歩` `駅近` `温泉街` | — |
| Get bored just staying in the hotel | 宿にこもるだけだと飽きる | `散策` `足湯` `温泉街` `市場` | — |
| Don't want to strain the body | 体に負担をかけたくない | `送迎` `貸切風呂` `客室露天` `個室` `禁煙` | — |
| Worried about getting around in winter | 冬の移動が不安 | `年末年始ダイヤ` `時刻表` `タクシー` | 雪国。年末年始ダイヤ |
| There should be a discount | 割引があるはず | `"キャンペーン"` `割引` `受付開始` | — |
| A restaurant where it's OK if the kids are loud | 子どもが騒いでも気まずくない店がいい | `座敷` `個室` `"お子様"` `子連れ` `-カウンターのみ` | — |
| Want to move around the kids' naps and moods | 子どもの昼寝・機嫌に合わせて動きたい | `授乳室` `ベビーカー` `屋内` `キッズスペース` | — |
| Don't want to get tired driving | 運転で疲れたくない | `道の駅` `駐車場` `インターから` | — |
| Don't want trouble parking | 駐車場で困りたくない | `駐車場あり` `無料駐車場` `提携駐車場` | — |
| Don't want to walk long in the heat | 暑い中を長く歩きたくない | `屋内` `駅直結` `アーケード` `涼しい` | — |
| Don't want to queue / avoid crowds | 並びたくない／人混みを避けたい | `予約可` `整理券` `時間指定` `穴場` | — |
| Not a big hotel / want a small inn | 大きいホテルは嫌／小さな宿がいい | `全○室` `離れ` `小さな宿` `-宴会場` `-バイキング` | 旅館は「全○室」と書くことが多い。○ は実際の数字で検索（`"全8室" OR "全10室"`） |
| Want dinner in the room or a private dining room | 部屋食か個室で食べたい | `部屋食` `"お部屋食"` `個室食事処` `個室料亭` | 部屋食は特定のプランだけのことが多い。「個室食事処」でも仕切りだけの場合がある |
| Want a private bath | 貸切風呂に入りたい | `貸切風呂` `貸切露天` `客室露天` `"無料"` | 貸切風呂は1回45〜50分・有料・チェックイン時に予約のことが多い |
| Not too expensive, but not cheap-looking | 高すぎないが安っぽいのは嫌 | `全○室` `リニューアル` `-バイキング` `-格安` | — |
| Don't want surprise extra charges | あとから追加料金で驚きたくない | `入湯税` `サービス料込` `"別途"` `お通し` `チャージ` `個室料` | 温泉地の宿（入湯税）。居酒屋はお通し・席料がつくことが多い |
| Old is fine if it's clean | 古くても清潔ならいい | `リニューアル` `改装` `禁煙` `洗浄機能付きトイレ` | 老舗旅館 |
| Want to sleep quietly at night | 夜は静かに眠りたい | `離れ` `全○室` `-宴会場` `-カラオケ` | 木造の宿で強く効く |
| Want a slow morning | 朝はゆっくりしたい | `"チェックアウト11時"` `レイトチェックアウト` `朝食なし` | — |
| Keep it around a budget per person | 一人あたり予算はこのくらい | `コース` `"料理のみ"` `"税込"` `予算` | 居酒屋はお通し・席料が別にかかることが多い。コース価格が飲み放題込みかどうかを見る |
| Someone in the group doesn't drink | 飲まない人がいる | `ノンアルコール` `ソフトドリンク` `"料理のみ"` | 「飲み放題付き」のみのコースが多い店は注意 |
| Want a private room | 個室がいい | `完全個室` `半個室` `個室` `"4名様"` | 「個室」とあっても半個室（仕切り・のれん）のことが多い。個室料・人数の下限を見る |
| Don't want cigarette smoke | たばこの煙は避けたい | `全席禁煙` `禁煙` `-喫煙可` | 2020年から原則屋内禁煙だが、小さな既存店や喫煙専用室・加熱式たばこ可の店がある |
| A restaurant that's easy to go to alone | 一人でも入りやすい店がいい | `カウンター` `"お一人様"` `定食` `-"2名様より"` | — |
| Eating with several people who like different things | 好みがばらばらな数人で食べたい | `一品料理` `単品` `席のみ予約` `-"コースのみ"` | — |
| Want it to be fun even if it rains | 雨でも楽しめるようにしたい | `屋内` `雨の日` `アーケード` `体験` `美術館` | 梅雨・台風の時期 |
