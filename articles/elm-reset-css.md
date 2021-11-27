---
title: "リセットCSSを我が手に（elm-reset-css）"
emoji: "🦾"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["Elm", "CSS"]
published: false
---

https://github.com/y047aka/elm-reset-css

# リセット CSS の未来

### 進化を続けるリセット CSS

sanitize.css 13.0.0 では、CSS の新しいセレクタ `:where()` を活用してスタイル指定の詳細度を上げないような工夫が採用されました。また、いくつかのリセット CSS では 2022 年 6 月の Internet Explorer サポート終了に先駆けて、IE 向けのリセット記述が削除されています。

だけど、「20XX 年のおすすめリセット 5 選」みたいなトレンドを追ったり、既存リセット CSS の最新バージョンが自分の目的に合ってるか調べたりするのは、なかなか大変です。ブラウザのスタイル指定をリセットするだけなのに。そんなに頑張る必要があるのかな...？

### elm-reset-css v3 を開発中です

elm-reset-css は Elm と組み合わせているので、リセット内容を動的に調整することできます。「フォーム部分だけリセットしたい」「margin や padding はリセットしたくない」などの調整を 1 つのリセット CSS でコントロールしたいと考えています。まずは sanitize.css と destyle.css を 2 種類をベースにして、[erc_HardReset] と [erc_Normalize] を作っています（WIP）。

もっと画期的な方法があるかもしれませんが、まずは小さな改良を少しずつ重ねていきます。

[erc_hardreset]: https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Html-ResetCss#erc_HardReset
[erc_normalize]: https://package.elm-lang.org/packages/y047aka/elm-reset-css/latest/Html-ResetCss#erc_Normalize

# Elm AdventCalendar 2021

この記事は Elm AdventCalendar 2021 の 1 日目として書きました。
カレンダーにはまだ空きがありますので、Elm を完全に理解してしまった人も、これから Elm 頑張るぞ！という人も、ぜひ記事を投稿してみてください 🙌

https://qiita.com/advent-calendar/2021/elm
