---
title: "elm-watch入門（2）"
emoji: "🔄"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Elm", "環境構築"]
published: true
---

この記事は [Elm Advent Calendar 2022](https://qiita.com/advent-calendar/2022/elm) の 4 日目の記事です。

---

[elm-watch 入門（1）] では [elm-watch] の最も簡単な導入方法を紹介しました。
今回は、開発サーバつきの環境を構築してみましょう。

[公式サンプル][elm-watch_example] では esbuild を活用する方法が示されていますが、複数アプリの同時実行など含んだ大きめのサンプルになっています。入門用にもう少しシンプルな例があると嬉しいですね。

ということで、開発サーバつきの環境構築に必要な部分を抜き出したものがこちらです。
（詰まるところがあれば [公式ドキュメント][document site] や [公式サンプル][elm-watch_example] なども参考にしてください）
https://github.com/y047aka/elm-app-templates/tree/main/elm-watch

以下、簡単に説明を書いてみます。

# ディレクトリ構成

一般的な Elm アプリケーションと大きな違いはありません。

- public/
  - static/
    - `logo.svg` ...画像を含むサンプルを作りたかったので追加
  - `index.html` ...（後述）
  - `style.css` ...CSS を含むサンプルを作りたかったので追加
- src/
  - `Main.elm`
- `.gitignore`
- `app.ts` ...esbuild で使います
- `elm-watch.json` ...前回の例から少し修正しました（後述）
- `elm.json`
- `package-lock.json`
- `package.json` ...esbuild を使うように書き換えました（後述）

# package.json

https://github.com/y047aka/elm-app-templates/blob/main/elm-watch/package.json

- `esbuild`を使うので、dependencies や scripts に追加しました
- [run-pty] は複数のコマンドを同時に実行するツールです
  - これも lydell さんが作っています
  - 別の方法で複数コマンドを実行できるのであれば、`run-pty` を使わなくても大丈夫です
    - ターミナルを 2 つ開いて `elm-watch hot` と `npm run esbuild` を個別に実行しても OK
- 個人の趣味で `elm-toolilng` を使わずに、直接 `elm` `elm-format` をインストールしています
  - 好きな方法を使ってください 👍

# elm-watch.json

https://github.com/y047aka/elm-app-templates/blob/main/elm-watch/elm-watch.json

- esbuild の開発サーバで `public` ディレクトリを指定したので、`output` のパスを書き換えています
- "My target name" のところはアプリを区別できる任意の文字列を入れてください
  - `elm-watch`で複数の Elm アプリケーションを実行する場合に使います（今回は使いません）
  - 詳細は [elm-watch.json - elm-watch](https://lydell.github.io/elm-watch/elm-watch.json/) を参照してください

# 動きましたー

以上の構成で開発サーバつきの環境を起動できると思います。

`elm-watch` では、アプリ実行中にコンパイルのモードを切り替えてタイムトラベルデバッガやコンパイル最適化の On/Off を簡単に切り替えられます。便利ですね。

まだ`elm-watch`の全ての機能を使いこなせていませんが、色々とカスタマイズ方法を学んで使ってみたいと思います。（コンパイル後の JS ファイルに postprocess を追加したりもできる）

# 次回予告

今回のサンプルは SPA のルーティングに対応していません。[公式サンプル][elm-watch_example]では自前の `dev-server.js` を用意して解決しているので、このあたりのコードを整理して使ってみたいと思います。

---

お知らせ：2023 年 1 月 7 日に Elm のオンラインイベントを開催します！
イベントの第 2 部は、みんなで Elm のアドベントカレンダーを読む会をしたい。

4 月には東京で現地開催のイベントも企画しようかなと考えています。

https://elm-jp.connpass.com/event/268596/

[elm-watch]: https://github.com/lydell/elm-watch
[document site]: https://lydell.github.io/elm-watch/
[elm-watch_example]: https://github.com/lydell/elm-watch/tree/main/example
[run-pty]: https://github.com/lydell/run-pty/
[elm-app-templates/elm-watch]: https://github.com/y047aka/elm-app-templates/tree/main/elm-watch
[elm-watch 入門（1）]: https://zenn.dev/y047aka/articles/elm-watch-01
