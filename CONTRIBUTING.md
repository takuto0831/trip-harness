# Contributing to the dictionary

English | [日本語](#日本語)

Add signals that worked on your trips to the shared dictionary. There are two parts:

| Part | File | What goes there |
|---|---|---|
| Core dictionary | `skills/where-to-harness/dictionary.md` | Unspoken preference / Observable signals / What the AI judges / How to confirm / When it applies. Language-independent |
| Locale pack | `skills/where-to-harness/locales/<locale>.md` | For each core entry: search and exclusion terms in the destination's language, and local conditions. Also the local booking and gourmet sites |

1. After a trip, the skill asks "Do you want to send this to the dictionary?" and shows a core row plus a locale row
2. **Check that no personal details are in it** (family health, names, a date-and-place combination)
3. Open an Issue and paste the rows (a PR is fine too)

### A new locale pack

Copy `locales/ja-JP.md`, name it after the country (e.g. `it-IT.md`, `en-US.md`), and fill in the terms for the core entries you know. You don't need every entry; the skill builds terms on the spot for missing ones.

### Rules

- No names of specific hotels or restaurants (generalized signals only)
- Don't paste review text (observable facts only)

Accepted entries ship with the next plugin update (the skill doesn't fetch the dictionary from the internet).

---

## 日本語

旅行で効いたシグナルを、みんなの辞書に足してください。辞書は 2 つに分かれています。

| 部分 | ファイル | 中身 |
|---|---|---|
| コア辞書 | `skills/where-to-harness/dictionary.md` | 暗黙知／観測シグナル／AI が判定すること／確認方法／当てはまる条件。言語に依存しない |
| 検索語パック | `skills/where-to-harness/locales/<locale>.md` | コア辞書の項目ごとの、行き先の言語の検索語・除外語と、その国の事情。予約・グルメサイトの一覧も |

1. 旅行のあとで、スキルが「辞書に送りますか？」と聞き、コア辞書の 1 行と検索語パックの 1 行を見せます
2. **個人の事情（家族の体調、人名、日付と場所の組み合わせ）が入っていないか**を確かめてください
3. Issue を立て、その行を貼ってください（PR でも構いません）

- 店や宿の固有名詞は書かない（一般化したシグナルだけ）
- 口コミの文章は貼らない（観測できる事実だけ）

採用した項目は、プラグインの次の更新で配られます（スキルは辞書をネットから取りにいきません）。
