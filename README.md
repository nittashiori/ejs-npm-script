# npm-scripts の web 制作向けタスクランナー

脱 gulp 用に作った web 制作コーディング用のファイル。

以下のサイトを参考に作成。

-   [Web 制作向け npm-scripts](https://qiita.com/takeshisakuma/items/dbbb1c465099e6e4dd2e#152-javascript%E3%82%92%E7%9B%B4%E6%8E%A5%E8%A8%98%E8%BF%B0%E3%81%99%E3%82%8B%E5%A0%B4%E5%90%88)

## 自動化内容

-   EJS を HTML ファイルに変換
-   Sass を CSS に変換
-   画像ファイルのデータ圧縮（TinyPng を使わなくても画像を自動圧縮する）
-   Browser-Sync によるオートリロード
-   CSS と js のファイル圧縮

## 使い方

-   `npm install` でパッケージをインストール。
-   `npm run dev` でローカル開発起動。
-   `npm run format:all` でファイル整形。（多分あまり使わない）
-   `npm run build` でフ公開用ファイルを出力。

## ファイル構造

css 設計は Flocss を採用。適宜使いやすいよう調整 OK。

参考

-   [[CSS 設計] 私のための FLOCSS まとめ](https://qiita.com/super-mana-chan/items/644c6827be954c8db2c0)

```
src
　├ _include // ejsで使う共通した内容を管理
    ├ _header.ejs
    └ _footer.ejs
  ├ ejs // ページはここで増やす
    ├ about
      └ index.ejs
    └ index.ejs
　├ js
    ├ common
      ├ _test1.js // 仮のファイルなので使うときは削除
      └ _test2.js // 仮のファイルなので使うときは削除
    └ index.js // 全てのjavascriptはここにimport
　├ scss
    ├ Foundation // サイト全体のデフォルトスタイルを管理。
      ├ base.scss // 土台となるスタイルを定義
      ├ destyle.scss // reset.css
      ├ mixins.scss // サイト全体で使えるmixnを管理
      └ variables.scss // サイト全体で使える変数を管理
    ├ Layout // 各ページを構成するサイト全体で共通したエリアを管理。
      ├ l-footer.scss
      └ l-header.scss
    ├ Object // サイト全体で再利用できるパターンを持つモジュールを管理
      ├ Component // 小さな単位のモジュールを管理
        └ c-logo.scss
      └ Project // Componentや他の要素によって構成される大きな単位のモジュールを管理
        └ p-card.scss
    ├ Utility // 調整のための便利クラスを管理
    └ style.scss // 全てのスタイルはここにimport
　└  static
    ├ img // 調整のための便利クラスを管理
      └ sample.jpg // 仮でいれてる画像なので削除
    └ webfont // 不要なら削除
```
