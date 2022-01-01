---
title: "[初稿] Elmの環境構築ガイド（2021）"
emoji: "⚖️"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Elm", "環境構築"]
published: true
---

:::message alert
この記事はまだ初稿です。新しく Elm を使う方に向けて、より充実した情報を提供したいと考えています。紹介している方法以外の環境構築方法をご存知の方は、この記事のコメント欄や [Pull Request](https://github.com/y047aka/zenn-docs/blob/main/articles/install-elm-2021.md) にて情報をお寄せください。
:::

Elm の開発環境を構築する方法はどのくらいあるでしょうか？

- **elm reactor**
- **elm-live**
- **webpack** および **create-elm-app**
- **Parcel**
- **esbuild** および **vite**
- npm-scripts を駆使する（**elm-starfighter**）

1 つずつ見ていきましょう。

:::message
この記事では、Elm の最低限のビルド方法を紹介します。

- [elm-language-server]
- [elm-format]
- [elm-review]
- [elm-test]
- [elm-json]

などのツールの解説は記事の対象外です。
:::

[elm-language-server]: https://github.com/elm-tooling/elm-language-server
[elm-format]: https://github.com/avh4/elm-format
[elm-review]: https://github.com/jfmengels/node-elm-review
[elm-test]: https://github.com/elm-explorations/test
[elm-json]: https://github.com/zwilias/elm-json

# elm reactor

`elm` のサブコマンド `elm reactor` を実行すると、開発サーバが起動します。とりあえず Elm を触ってみたい場合は、これを使ってみると良いでしょう。

### 特徴

- Elm をインストールするだけで使える
- 開発を進めると物足りなくなってくる（CSS の組み込みに手間がかかるなど）

> `elm reactor`を使うと、ターミナルで毎度ごちゃごちゃ頑張らなくても Elm プロジェクトをビルドできます。次のように、プロジェクトのルートディレクトリで以下のコマンドを入力してみてください。
>
> ```bash
> elm reactor
> ```
>
> サーバーが[`http://localhost:8000`](http://localhost:8000)で起動します。このサイトではどの Elm ファイルにも移動できて、どんな感じになるか見ることができます。`elm reactor`を実行して、localhost へのリンクを開き、`src/Main.elm`ファイルを確認してみてください！
>
> （Elm 公式のガイド「[Elm をインストールする（日本語版）](https://guide.elm-lang.jp/install/elm.html)」より引用）

### 環境構築例

https://github.com/y047aka/elm-app-templates/tree/main/elm_reactor

# elm-live

開発サーバーを起動し、Elm ファイルの変更をリアルタイムに検知してレンダリングしてくれます。`elm make`コマンドを`elm-live`に置き換えて、簡単に使い始めることができます。
elm-live すき！

https://github.com/wking-io/elm-live

公式ドキュメントが充実していて嬉しいです、読みましょう。`elm make` コマンドのオプションをそのまま使えて嬉しい！
https://www.elm-live.com

# webpack および create-elm-app

webpack で Elm を扱うためのローダーが提供されています。

https://github.com/elm-community/elm-webpack-loader

webpack を使いたい人には、[create-elm-app] も選択肢になるかもしれません。

https://github.com/halfzebra/create-elm-app

[create-elm-app]: https://github.com/halfzebra/create-elm-app

# Parcel

Elm も公式にサポートされています。

https://parceljs.org/languages/elm/

v1 の頃に少し使っていました。v2 でも引き続き動作するようです。
https://github.com/y047aka/elm-chagama/tree/main/parcel

# esbuild および vite

https://text.hmsk.me/entries/2020-10-19/

サンプルプロジェクトを参考にするのが良さそうです。
https://github.com/hmsk/vite-plugin-elm/tree/main/example

# npm-scripts を駆使する（elm-starfighter）

何らかの理由によって、これらの方法を選択できないことがあるかもしれません。
モジュールバンドラーを使わない場合にはどうしたら良いのでしょうか？

設定や起動を npm-scripts で完結する [elm-starfighter] を公開しているので、困ったことがあれば使ってみてください。内部では elm-live やなどのパッケージを npm scripts で組み合わせて使っています。

https://y047aka.space/posts/elm-starfighter/

[elm-starfighter]: https://github.com/y047aka/elm-starfighter
