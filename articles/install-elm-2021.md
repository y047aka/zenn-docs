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
- **Ellie (Elm Live Editor)**
- **elm-live**
- **webpack**
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

# Ellie (Elm Live Editor)

`elm reactor` と同等の機能をオンラインで利用できます。ローカルに開発環境を構築するのが面倒な場合にはこちらが便利です。

> Ellie(Elm Live Editor)はオンラインで Elm アプリを作成・シェアできるサイトです。
> （書籍『[基礎からわかる Elm]』より引用）

https://ellie-app.com/

[基礎からわかる Elm]: https://www.c-r.com/book/detail/1299

### 特徴

- Elm Packages に公開されているパッケージも利用できる
- コードのフォーマット機能やシェア用のリンク発行機能あり
- CSS や他のファイルを読み込む場合には不向き

# elm-live

開発サーバーを起動し、Elm ファイルの変更をリアルタイムに検知してレンダリングしてくれます。`elm make`コマンドを`elm-live`に置き換えて、簡単に使い始めることができます。

https://www.elm-live.com

### 特徴

- CSS の読み込みや、Hot Module Replacement など、必要十分な開発環境を構築できる
- `elm make` のオプションを同じように使える
- Elm 以外のライブリロードはサポートしていない

### 環境構築例

https://github.com/y047aka/elm-app-templates/tree/main/elm-live

※ Elm 以外のビルドには他のライブラリを使用し、 npm scripts で実行を管理しています。

# webpack

webpack で Elm を扱うためのプラグイン [elm-webpack-loader] が公開されています。既に webpack を使い慣れている場合は、これを活用すると良いでしょう。

[elm-webpack-loader]: https://github.com/elm-community/elm-webpack-loader

### 特徴

- 設定次第で環境を細かく制御できる
- `webpack.config.js` の設定が大変

### 環境構築例

https://github.com/y047aka/elm-app-templates/tree/main/webpack

細かい設定は、[create-elm-app] などを参考にしてください。

[create-elm-app]: https://github.com/halfzebra/create-elm-app

# Parcel

### 特徴

- 設定ファイル不要（zero config）で動作する
- Elm もサポートされている（ https://parceljs.org/languages/elm/ ）


### 環境構築例

https://github.com/y047aka/elm-app-templates/tree/main/parcel

# esbuild および vite

https://text.hmsk.me/entries/2020-10-19/

サンプルプロジェクトを参考にするのが良さそうです。
https://github.com/hmsk/vite-plugin-elm/tree/main/example
