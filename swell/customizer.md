# SWELL Customizer map

Status: **checked 2026-10-17** against the SWELL manual (swell-theme.com/basic-setting/… pages; written 2021-08 for SWELL 2.x and still the official reference; SWELL is still 2.19, 2026-08-20). Item labels can differ slightly in the 2.19 Customizer: confirm on the site before handing over a path.

外観 → カスタマイズ

| Panel | Sections |
|---|---|
| サイト全体設定 | 基本カラー (メインカラー / テキストカラー / リンクカラー / 背景色; no accent colour here) · 基本デザイン (フォント設定 / コンテンツ幅の設定: サイト幅・記事コンテンツ幅 / サイト全体の見た目) · スマホ開閉メニュー · お知らせバー · タイトルデザイン |
| ヘッダー | カラー設定 · ヘッダーロゴ画像の設定 (height) · レイアウト・デザイン設定 (PC 4 types / SP 3 types) · トップページでの特別設定 (transparent header) · ヘッダーの追従設定 · ヘッダーバー設定 · ヘッダーメニュー (hover effect) · 検索ボタン · スマホヘッダーのボタン. Menu items themselves: 外観 → メニュー (locations グローバルナビ, スマホ用ヘッダー) |
| フッター | フッターのカラー設定 (背景色 / 文字色) · コピーライトの設定 · その他の設定. Footer widgets: 外観 → ウィジェット (フッター(PC)1〜3, フッター(スマホ)) |
| トップページ | メインビジュアル (image / video / slider up to 5, height, filter) · 記事スライダー · ピックアップバナー |
| 記事一覧リスト | リストレイアウト (カード型, リスト型, リスト型（左右交互）, ブログ型, サムネイル型 ×2) · 最大カラム数 (PC / SP) |
| 投稿・固定ページ | タイトル (placement, date, category) · コンテンツのデザイン (見出し2〜4, ボタン, マーカー, ブログカード, 引用) · 記事下エリア (SNS, prev/next, author, related, comments) |
| アーカイブページ | archive titles and lists |

Line height is not named in the manual's 基本デザイン page; check the live Customizer before giving a value.

## Handing over settings

List each one as a path and a value so a person can set it without guessing:

```
カスタマイズ → サイト全体設定 → 基本カラー → メインカラー: #1A56A0
カスタマイズ → サイト全体設定 → 基本デザイン → コンテンツ幅の設定 → サイト幅: 1120px
カスタマイズ → ヘッダー → ヘッダーロゴ画像の設定 → 画像の高さ(PC): 40px
```

Values come from the project's `DESIGN.md` (`../design/design-tokens.md`).
