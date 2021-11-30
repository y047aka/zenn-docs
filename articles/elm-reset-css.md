---
title: "リセットCSSを我が手に（elm-reset-css）"
emoji: "🦾"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Elm", "CSS"]
published: false
---

リセット CSS を切替・比較できるページを作りました！

https://y047aka.github.io/elm-reset-css/

- [Eric Meyer’s Reset CSS](https://meyerweb.com/eric/tools/css/reset/)
- [html5doctor.com Reset Stylesheet](https://github.com/richclark/HTML5resetCSS)
- [destyle.css](https://github.com/nicolas-cusan/destyle.css)
- [Normalize.css](https://github.com/necolas/normalize.css)
- [ress](https://github.com/filipelinhares/ress)
- [sanitize.css](https://github.com/csstools/sanitize.css)
- [The New CSS Reset](https://github.com/elad2412/the-new-css-reset)

この記事では、このページで使っている自作パッケージ、 [y047aka/elm-reset-css] を紹介します。

[y047aka/elm-reset-css]: https://github.com/y047aka/elm-reset-css

# elm-reset-css

y047aka/elm-reset-css は Elm のパッケージです。いくつかの人気のあるリセット CSS を `Html msg` 型で再実装し、Elm で簡単に扱えるようにしました。1 つのパッケージにまとめたので、呼び出す関数を変えるだけでリセット CSS を簡単に切り替えることができます。

https://github.com/y047aka/elm-reset-css

#### elm-css でも使えます

CSS 部分の実装には [elm-css] を使用しているので、`List Snippet` 型でも扱えるようにしてあります。[^1] 最近は [elm-ui] でも使いやすいように `Element msg` 型を提供することも考えています。

[elm-css]: https://github.com/rtfeldman/elm-css
[elm-ui]: https://package.elm-lang.org/packages/mdgriffith/elm-ui/latest/

#### リセット CSS の過去バージョンも使えます

sanitize.css、ress、destyle.css の３種類について、直近の複数バージョンを提供しています。

- [Css.Reset.Sanitize (latest, v12)](https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Css-Reset-Sanitize)
- [Css.Reset.Ress (latest, v3, v2)](https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Css-Reset-Ress)
- [Css.Reset.Destyle (latest, v2)](https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Css-Reset-Destyle)

# リセット CSS の未来

#### 進化を続けるリセット CSS

sanitize.css 13.0.0 では、CSS の新しいセレクタ `:where()` を活用してスタイル指定の詳細度を上げないような工夫が採用されました。また、いくつかのリセット CSS では 2022 年 6 月の Internet Explorer サポート終了に先駆けて、IE 向けのリセット記述が削除されています。

けれど、「20XX 年のおすすめリセット 5 選」みたいなトレンドを追ったり、既存リセット CSS の最新バージョンが自分の目的に合ってるか調べたりするのは、なかなか大変です。ブラウザのスタイル指定をリセットするだけなのに。

#### elm-reset-css v3 を開発中です

elm-reset-css は Elm と組み合わせているので、リセット内容を動的に調整することできます。「フォーム部分だけリセットしたい」「margin や padding はリセットしたくない」などの調整を 1 つのリセット CSS でコントロールしたいと考えています。[^2]

[erc_hardreset]: https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Html-ResetCss#erc_HardReset
[erc_normalize]: https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Html-ResetCss#erc_Normalize

# Elm AdventCalendar 2021

この記事は Elm AdventCalendar 2021 の 1 日目として書きました。
カレンダーにはまだ空きがありますので、Elm を完全に理解してしまった人も、これから Elm 頑張るぞ！という人も、ぜひ記事を投稿してみてください 🙌

https://qiita.com/advent-calendar/2021/elm

[^1]: というよりは elm-css で使いたかったのでこのパッケージを作りました。
[^2]: まずは sanitize.css と destyle.css を 2 種類をベースにして、[erc_HardReset] と [erc_Normalize] を作っています（WIP）。
