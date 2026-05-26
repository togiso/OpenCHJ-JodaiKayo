# OpenCHJ-上代歌謡データ
「仏足石歌」と「歌経標式」引用歌のテキストにUniDicによる短単位の形態論情報を付与し、誤りを修正したものです。
「仏足石歌」は [Wikipedia「仏足跡歌碑」](https://ja.wikipedia.org/wiki/%E4%BB%8F%E8%B6%B3%E8%B7%A1%E6%AD%8C%E7%A2%91) のテキストをもとにしています。
「歌経標式」引用歌は [Oxford NINJAL Corpus of Old Japanese (ONCOJ)](https://oncoj.ninjal.ac.jp/) の（ローマ字）テキストをひらがなに変換して作成しています。
いずれも漢字のみの原文をフリガナの形で取り込んで「中納言」で表示されるようにしています。

歌経標式の形態論情報の整備に当たっては[『歌経標式―注釈と研究』沖森卓也（1993）おうふう](https://ndlsearch.ndl.go.jp/books/R100000002-I000002256646) を参考にしました。

## 形態論情報 ファイル形式
- UTF-8 (BOMなし) LF改行, タブ区切り
- フィールド（左から）
  - ファイル名（作者 作品名）
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

### テキストデータライセンス
- テキストデータのライセンスは原データに従ってください。
  - 仏足石歌（Wikipedia）は[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  - 歌経標式（ONCOJ）は[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

