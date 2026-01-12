---
title: "関数型まつり2026のWebサイトをGleamで開発中！"
emoji: "🎪"
type: "idea" # tech: 技術記事 / idea: アイデア
topics: ["gleam", "lustre", "fpmatsuri"]
published: false
---

昨年6月に開催した『関数型まつり』から半年が経ちました。
2026年の開催に向けて、私はPRチームを担当する座長に就任し、本格的な準備のキックオフに向けてWebサイトを整備しています。

https://2026.fp-matsuri.org/


## 今年はGleamを使ってみます

昨年はElm（elm-pages）で実装しましたが、2026年は [Gleam](https://gleam.run/) を試してみることにしました。Webサイトに関数型言語を採用することで、スタッフとしての活動にも興味を持ってもらえたら嬉しいです。


Gleamの公式サイトにはElmユーザーに向けたチートシートも用意されています。ありがとう！
https://gleam.run/cheatsheets/gleam-for-elm-users/

Elmに大きな不満はありません。もしGleamでの開発に行き詰まってしまったら、Elmに戻すと思います。

## 技術構成

https://github.com/fp-matsuri/2026.fp-matsuri.org

現在の技術スタックは以下のとおりです：

| カテゴリ | 技術 |
|---------|------|
| 言語 | Gleam |
| フレームワーク | Lustre |
| スタイリング | Tailwind CSS + daisyUI |
| テスト | Playwright（主にビジュアルリグレッション） |
| 環境構築 | Nix |


## Gleamを使ってみた所感

[Lustre](https://hexdocs.pm/lustre/) はGleamでWebアプリを開発するためのフレームワークで、The Elm Architectureを採用しています。Elmに慣れた身としてはとても馴染みやすく、実装の記述はスムーズに進んでいます。

日本語の情報はまだ少ないものの、[@comamoca](https://zenn.dev/comamoca) さんの投稿やブログではGleamやLustreに関する実践的な記事が公開されており、とても参考になりました。公式ドキュメントも充実しているので、スムーズにキャッチアップできると思います。

最近は [lustre_ssg](https://github.com/lustre-labs/ssg) の導入に取り組んでいます。上手くいくかどうか、ちょっと不安。

## 企画・運営スタッフを募集しています

「今年も関数型まつりを楽しみたい」という皆さん、スタッフとして一緒に活動しませんか？
Webサイトの開発だけでなく、多くのスタッフの協力で関数型まつりが開催されます！

![関数型まつり2026のチーム紹介](/images/fp-matsuri_2026_recruiting.png)

1月18日（土）19:00〜21:00にオンラインでキックオフミーティングを開催します。
以下のconnpassページからお申し込みください。

https://jsa.connpass.com/event/380068/

---

PRチームのスタッフとして活動した昨年の振り返り：
[関数型まつりをスタッフ視点で振り返る](https://y047aka.github.io/posts/fp-matsuri_2025)
