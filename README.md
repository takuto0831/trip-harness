# trip-harness

旅行計画を、**人の暗黙知と AI の裏取りを往復させて**進める Claude Code のスキル。

「うるさくない店がいい」「チェーンは嫌」「宿にこもるだけだと飽きる」のような曖昧な感覚を検索語・除外語に翻訳し、AI が Web 検索と宿・店の公式サイトで候補を探して、制約ごとの比較表とおすすめを出します。検索でわからないことは「未確認」として、電話で聞くことのリストにします。

- 自分で探したいときは、そう言えば検索リンク（Google 検索・Google マップ）を渡します。見てきた店名・リンク・スクショを貼れば、同じ基準で判定します
- AI は予約サイト・グルメサイトのページを自動で取りにいきません。料金・空室・口コミは、渡したリンクからあなたが見ます
- API キーや外部サービスの設定は要りません
- 既定は会話だけで進めます。「保存して」と言えば、作業フォルダに Markdown の台帳（制約・候補・確認タスク・判断・旅程）を作り、会話をやり直しても続きから始められます

## 入れ方（Claude Code）

```
/plugin marketplace add takuto0831/trip-harness
/plugin install trip-harness@trip-harness
```

`/plugin` が使えない環境（VS Code 拡張など）では、ターミナルで同じことができます。

```
claude plugin marketplace add takuto0831/trip-harness
claude plugin install trip-harness@trip-harness
```

入れたあとは Claude Code を開き直してください。

### 新しい版に更新する

```
claude plugin marketplace update trip-harness
claude plugin update trip-harness@trip-harness
```

## 使い方

Claude Code を開き、「旅行の計画を一緒に考えて」と話しかけます。保存するつもりなら、この repo ではなく旅行用のフォルダで開いてください（記録はそのフォルダにできます）。

## 中身

- `skills/trip-harness/SKILL.md` … スキル本体
- `skills/trip-harness/dictionary.md` … 暗黙知 → シグナル変換辞書（プラグインに同梱。項目の送り方は [CONTRIBUTING.md](CONTRIBUTING.md)）
- `skills/trip-harness/templates/` … 旅行フォルダのひな形
