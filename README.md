# OpenCHJ-上代歌謡データ
「仏足石歌」と「歌経標式」引用歌のテキストにUniDicによる短単位の形態論情報を付与し、誤りを修正したものです。
「仏足石歌」は [Wikipedia「仏足跡歌碑」](https://ja.wikipedia.org/wiki/%E4%BB%8F%E8%B6%B3%E8%B7%A1%E6%AD%8C%E7%A2%91) のテキストをもとにしています。
「歌経標式」例歌は [Oxford NINJAL Corpus of Old Japanese (ONCOJ)](https://oncoj.ninjal.ac.jp/) の（ローマ字）テキストをひらがなに変換して作成しています。
いずれも漢字のみの原文をフリガナの形で取り込んで「中納言」で表示されるようにしています。

歌経標式の形態論情報の整備に当たっては[『歌経標式―注釈と研究』沖森卓也（1993）おうふう](https://ndlsearch.ndl.go.jp/books/R100000002-I000002256646) を参考にしました。

## 形態論情報 ファイル形式
- UTF-8 (BOMなし) LF改行, タブ区切り
- フィールド（左から）
  - ファイル名（資料名）
  - サブコーパス名
  - 開始文字位置（ファイル頭からのオフセット値*10）
  - 終了文字位置（同上）
  - 文境界（B=文頭）
  - 書字形出現形（=キー, 表層形）
  - 語彙素
  - 語彙素読み
  - 品詞
  - 活用型
  - 活用形
  - 発音形
  - 語種

### 形態論情報ライセンス
- [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## テキスト（XML）データ
簡易なOpenCHJ-XML形式である[OCX mini 文書定義](https://openchj.github.io/ocx-mini)にあわせて作成したXMLファイルです。万葉仮名の原文を表示するためにルビを利用しました。

- [Bussokusekika_ocx-mini.xml](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/Bussokusekika_ocx-mini.xml)

- [kakyo_hyoshiki_ocx-mini.xml](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/kakyo_hyoshiki_ocx-mini.xml)

このXMLでは、文書全体を `<doc>` 要素で囲み、OCX mini の名前空間 `https://openchj.github.io/ns/ocx` をデフォルト名前空間として指定しています。各歌は和歌一首を表す単位として `<lg type="waka">` で記述し、歌番号は `id` 属性として保持しました。

万葉仮名の本文は `<r>` 要素の内容として記述し、その読みを `rt` 属性に記録しています。たとえば `<r rt="あ">阿</r>` のように、要素内容が解析対象となる本文文字、`rt` 属性がその読みを表します。この方式により、万葉仮名の表記を本文として保持しつつ、読みを本文文字列から分離して記録しています。

OCX mini で定義されていない要素については、TEI のタグセットを利用しています。具体的には、和歌一首を表す `<lg type="waka">`、句切れを表す `<caesula/>`、判読不能・欠損・空白等を示す `<unclear>` は、TEI の詩歌・翻刻記述の考え方に基づいて用いています。

歌中の句切れは `<caesula/>` で示しました。これは和歌内部の韻律的・構造的な切れ目を表すための空要素です。また、判読不能・欠損・空白等を示す箇所は `<unclear>` 要素で示し、元データの内容をそのまま保持しています。

各 `<lg type="waka">` の末尾には `<eos/>` を置き、一首ごとの解析上の区切りを明示しました。これにより、OpenCHJ の形態素解析・検索処理において、一首を一つの文相当の単位として扱えるようにしています。

## 使用している主なタグ

### OCX mini のタグ

| 要素・属性 | 用途 |
|---|---|
| `<doc>` | OCX mini 文書全体を表すルート要素 |
| `<r>` | ルビ付き本文文字を表す要素 |
| `rt` | `<r>` 要素に対応する読み |
| `<eos/>` | 解析上の文末・一首末を表す境界マーカー |

### TEI のタグ

| 要素・属性 | 用途 |
|---|---|
| `<lg type="waka">` | 歌一首を表す要素 |
| `id` | 各歌の歌番号 |
| `<caesula/>` | 歌中の句切れを表す空要素 |
| `<unclear>` | 判読不能・欠損・空白等の不確実な箇所 |


### テキストデータライセンス
- テキストデータのライセンスは原データに従ってください。
  - 仏足石歌（Wikipedia）は[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  - 歌経標式（ONCOJ）は[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

