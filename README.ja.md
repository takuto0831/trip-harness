# where-to-harness

[English](README.md) | 日本語

**行きたい場所**を、人の暗黙知と AI の裏取りを往復させて探すスキル。Claude Code と Codex に入れられます（動作を確かめたのは Claude Code だけです）。

こんなときに使えます。

- **旅行**: どこに泊まるか、どのエリアにするか、何をするか。旅程づくりまで
- **食事**: 旅行じゃなくても、お店探しだけで使えます。たとえば「金曜に4人で、東京で静かめの居酒屋。チェーンは嫌」

「うるさくない店がいい」「チェーンは嫌」「宿にこもるだけだと飽きる」のような曖昧な感覚を検索語・除外語に翻訳し、AI が Web 検索と宿・店の公式サイトで候補を探して、制約ごとの比較表とおすすめを出します。検索でわからないことは「未確認」として、電話で聞くことのリストにします。

- 自分で探したいときは、そう言えば検索リンク（Google 検索・Google マップ）を渡します。見てきた店名・リンク・スクショを貼れば、同じ基準で判定します
- AI は予約サイト・グルメサイトのページを自動で取りにいきません。料金・空室・口コミは、渡したリンクからあなたが見ます
- API キーや外部サービスの設定は要りません
- 検索語は、話す言語ではなく**行き先の言語**で作ります。日本の旅行なら同梱の日本語の検索語パックを使い、パックの無い国ではその場で現地の言葉の検索語を組み立てます
- 既定は会話だけで進めます。「保存して」と言えば、作業フォルダに Markdown の台帳（制約・候補・確認タスク・判断・旅程）を作り、会話をやり直しても続きから始められます

## 入れ方（Claude Code）

ターミナルで次を実行します。

```
claude plugin marketplace add takuto0831/where-to-harness
claude plugin install where-to-harness@where-to-harness
```

入れたあとは Claude Code を開き直してください。

### 新しいバージョンに更新する

```
claude plugin marketplace update where-to-harness
claude plugin update where-to-harness@where-to-harness
```

## 入れ方（Codex）

Codex では Claude Code のプラグインは使えませんが、Codex にもとからある skill-installer で、この repo からスキルのフォルダを直接入れられます。Codex にこう頼んでください。

```
$skill-installer https://github.com/takuto0831/where-to-harness/tree/main/skills/where-to-harness
```

`~/.codex/skills/where-to-harness` に入ります。入れたあとは Codex を開き直してください。スキルは Web 検索を使うので、Codex で Web 検索を有効にしておいてください。

新しいバージョンにするときは、`~/.codex/skills/where-to-harness` を消してから、同じコマンドをもう一度実行します。

## 使い方

Claude Code を開き、「旅行の計画を一緒に考えて」や「今夜渋谷で居酒屋を探して」と話しかけます。保存するつもりなら、この repo ではなく旅行・おでかけ用のフォルダで開いてください（記録はそのフォルダの `outings/` にできます）。

> **注意: `WebFetch(domain:*)` を deny に入れないでください。** Claude Code の設定（`settings.json` の `permissions.deny`）に `WebFetch(domain:*)` があると、すべてのページ取得が拒否され、スキルが宿や店の公式サイトを読めません。いつも検索結果だけで判断することになり、「公式」で確かめた ○ が付かなくなります。避けたいサイトがあるときは、ドメインを個別に deny に入れてください。

## 中身

- `skills/where-to-harness/SKILL.md` … スキル本体
- `skills/where-to-harness/dictionary.md` … コア辞書。暗黙知 → 観測シグナル・AI が判定すること・確認方法（言語に依存しない部分）
- `skills/where-to-harness/locales/` … 行き先ごとの検索語パック。日本は `ja-JP.md`（検索語・除外語、日本の事情、予約・グルメサイト）。項目の送り方は [CONTRIBUTING.md](CONTRIBUTING.md)
- `skills/where-to-harness/templates/` … おでかけ（旅行・食事）ごとのフォルダのひな形
