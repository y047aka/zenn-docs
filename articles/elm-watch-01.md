---
title: "elm-watch入門（1）"
emoji: "🔄"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Elm", "環境構築"]
published: true
---

この記事は [Elm Advent Calendar 2022](https://qiita.com/advent-calendar/2022/elm) の 3 日目の記事です。

---

[elm-watch](https://github.com/lydell/elm-watch) は、一言で表現するなら「watch モード付きの `elm make`」です。Elm ファイルの変更を検知して再コンパイルし、ブラウザでのホットリロードを実現することに集中したライブラリです。

- リポジトリ：[lydell/elm-watch: `elm make` in watch mode. Fast and reliable.](https://github.com/lydell/elm-watch)
- 公式ドキュメント：[Home - elm-watch](https://lydell.github.io/elm-watch/)

この記事では elm-watch の最も簡単な導入方法を紹介します。

# あらすじ

- Elm のライブリロードや HMR（Hot Module Replacement）を実現する方法は、これまでも複数存在していました

  - [elm-live](https://github.com/wking-io/elm-live)は elm-watch と同様 Elm のみに集中したライブラリで、開発サーバが付属している点で elm-watch よりも少しリッチでした

    - 残念ながら、2021/03/07 の更新を最後にメンテナンスが停止しています
    - 今までありがとう！

  - webpack や Parcel のようなバンドルツールを使った方法も普及しています
    - 最近だと Vite が台頭していますね
      - ちょっとバグがあるっぽい？（自分であまり使わないので分からない）

- 2022/09/09 に Elm の [Discourse](https://discourse.elm-lang.org/t/introducing-elm-watch-elm-make-in-watch-mode-fast-and-reliable/8653) で elm-watch が発表されました！

# 使い方

Elm の開発環境にインストール
※ Node.js v14 以上が必要です（Windows だと v16 以上がサポート対象とのこと）

```
npm install elm-watch
```

init で `elm-watch.json` を生成（ディレクトリ構造は適宜調整してください）

```
npx elm-watch init
```

起動（`index.html` はブラウザで直接開きます）

```
npx elm-watch hot
```

詳細は、公式ドキュメントや Simon Lydell さん自身の動画解説をご覧ください。

- 公式ドキュメント：[Getting started - elm-watch](https://lydell.github.io/elm-watch/getting-started/)
- 動画：[Getting started with elm-watch - YouTube](https://youtu.be/n15nOCZnTac)
- 最小構成の例：[elm-watch/example-minimal at main · lydell/elm-watch](https://github.com/lydell/elm-watch/tree/main/example-minimal)

# elm-watch が実現すること / 実現しないこと

公式ドキュメントを読んでみましょう。

- [What elm-watch is - elm-watch](https://lydell.github.io/elm-watch/what-elm-watch-is/)
- [What elm-watch is not - elm-watch](https://lydell.github.io/elm-watch/what-elm-watch-is-not/)

# 開発サーバほしいー

自分で用意することになります。
[公式サンプル](https://github.com/lydell/elm-watch/tree/main/example)では esbuild を活用する方法が示されていますが、少しサンプルが大きいので最低限必要な部分を抜き出して解説記事を用意するつもりです。

---

お知らせ：2023 年 1 月 7 日に Elm のオンラインイベントを開催します！
イベントの第 2 部は、みんなで Elm のアドベントカレンダーを読む会をしたい。

4 月には東京で現地開催のイベントも企画しようかなと考えています。

https://elm-jp.connpass.com/event/268596/
