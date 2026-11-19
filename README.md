# OpenCHJ-上代歌謡データ
「仏足石歌」と「歌経標式」引用歌のテキストにUniDicによる短単位の形態論情報を付与し、誤りを修正したものです。
「仏足石歌」は [Wikipedia「仏足跡歌碑」](https://ja.wikipedia.org/wiki/%E4%BB%8F%E8%B6%B3%E8%B7%A1%E6%AD%8C%E7%A2%91) のテキストをもとにしています。
「歌経標式」例歌は [Oxford NINJAL Corpus of Old Japanese (ONCOJ)](https://oncoj.ninjal.ac.jp/) の（ローマ字）テキストをひらがなに変換して作成しています。
いずれも漢字のみの原文をフリガナの形で取り込んで「中納言」で表示されるようにしています。

歌経標式の形態論情報の整備にあたっては[沖森卓也ほか（1993）『歌経標式―注釈と研究』桜楓社](https://ndlsearch.ndl.go.jp/books/R100000002-I000002256646) を参考にしました。

## 形態論情情報
[上代語UniDic](https://clrd.ninjal.ac.jp/unidic/download_all.html#unidic_jodai)を使って形態素解析を行った上で誤りを修正したデータです。[OpenCHJ中納言](https://chunagon.ninjal.ac.jp/open-chj/)のデータソースに相当します。

- 仏足石歌 [Bussokusekika_morph.txt](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/Bussokusekika_morph.txt)

- 歌経標式例歌 [KakyoHyoshiki_morph.txt](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/KakyoHyoshiki_morph.txt)

### ファイル形式
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
- 作成者：小木曽智信
- [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

## テキスト（XML）データ
OpenCHJ-XML 形式である [OCX Standard](https://openchj.github.io/ocx-standard)（v0.62β）にあわせて作成したXMLファイルです。`ocx:doc` をルート要素とし、その中で TEI の語彙を使う書き方の見本でもあります。万葉仮名の原文を表示するためにルビを利用しました。

- 仏足石歌 [Bussokusekika_ocx-standard.xml](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/Bussokusekika_ocx-standard.xml)

- 歌経標式例歌 [KakyoHyoshiki_ocx-standard.xml](https://github.com/togiso/OpenCHJ-JodaiKayo/blob/main/KakyoHyoshiki_ocx-standard.xml)

このXMLでは、文書全体を `<ocx:doc>` 要素で囲んでいます。OCX の要素には接頭辞 `ocx:`（名前空間 `https://openchj.github.io/ns/ocx`）、TEI の要素には接頭辞 `tei:`（名前空間 `http://www.tei-c.org/ns/1.0`）を付けています。TEI 文書そのものではないため、TEI ヘッダーはありません。

```xml
<ocx:doc textID="仏足石歌" corpusName="上代歌謡" version="0.62"
         xmlns:ocx="https://openchj.github.io/ns/ocx"
         xmlns:tei="http://www.tei-c.org/ns/1.0">
<tei:lg n="1" type="waka"><ocx:r rt="美">み</ocx:r><ocx:r rt="阿">あ</ocx:r>…<tei:caesura/>…<ocx:eos/></tei:lg>
…
</ocx:doc>
```

各歌は和歌一首を表す単位として `<tei:lg type="waka">` で記述し、歌番号は `n` 属性として保持しました。

本文はひらがなにした解析対象のテキストを `<ocx:r>` 要素の内容として記述し、万葉仮名の原文を `rt` 属性に記録しています。たとえば `<ocx:r rt="阿">あ</ocx:r>` のように、万葉仮名の原文を振り仮名として、本文文字列から分離して記録しています。

OCX で定義されていない要素については、TEI のタグセットを利用しています。具体的には、和歌一首を表す `<tei:lg type="waka">`、句切れを表す `<tei:caesura/>`、判読不能・欠損・空白等を示す `<tei:unclear>` です。

歌中の句切れは `<tei:caesura/>` で示しました。これは和歌内部の韻律的・構造的な切れ目を表すための空要素です。また、判読不能・欠損・空白等を示す箇所は `<tei:unclear>` 要素で示し、元データの内容をそのまま保持しています。

各 `<tei:lg type="waka">` の末尾には `<ocx:eos/>` を置き、一首ごとの解析上の区切りを明示しました。これにより、OpenCHJ の形態素解析・検索処理において、一首を一つの文相当の単位として扱えるようにしています。

OCX Standard のスキーマ（[ocx-standard-tei.xsd](https://openchj.github.io/schema/ocx/standard/0.6/ocx-standard-tei.xsd) と [ocx-standard.sch](https://openchj.github.io/schema/ocx/standard/0.6/ocx-standard.sch)）で検証できます。

## 使用している主なタグ

### OCX のタグ

| 要素・属性 | 用途 |
|---|---|
| `<ocx:doc>` | 解析対象の本文全体を囲むルート要素 |
| `<ocx:r>` | ルビ付き本文文字を表す要素 |
| `rt` | `<ocx:r>` 要素の本文に対応する万葉仮名の原文 |
| `<ocx:eos/>` | 解析上の文末・一首末を表す境界マーカー |

### TEI のタグ

| 要素・属性 | 用途 |
|---|---|
| `<tei:lg type="waka">` | 歌一首を表す要素 |
| `n` | 各歌の歌番号 |
| `<tei:caesura/>` | 歌中の句切れを表す空要素 |
| `<tei:unclear>` | 判読不能・欠損・空白等の不確実な箇所 |


### テキストデータライセンス
- テキストデータのライセンスは原データに従ってください。
  - 仏足石歌（Wikipedia）は[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  - 歌経標式（ONCOJ）は[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

