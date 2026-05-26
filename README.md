# OpenCHJ-上代歌謡 形態論情報データ
「仏足石歌」と「歌経標式」引用歌のテキストにUniDicによる短単位の形態論情報を付与し、誤りを修正したものです。
「仏足石歌」は [Wikipedia「仏足跡歌碑」](https://ja.wikipedia.org/wiki/%E4%BB%8F%E8%B6%B3%E8%B7%A1%E6%AD%8C%E7%A2%91) のテキストをもとにしています。
「歌経標式」引用歌は [Oxford NINJAL Corpus of Old Japanese (ONCOJ)](https://oncoj.ninjal.ac.jp/) の（ローマ字）テキストをひらがなに変換して作成しています。
いずれも漢字のみの原文をフリガナの形で取り込んで「中納言」で表示されるようにしています。

## ファイル形式
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

## 形態論情報ライセンス
- [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

- テキストデータのライセンスは出典に従ってください。
  - Wikipediaは[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/)
  - ONCOJは[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)

