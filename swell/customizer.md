# SWELL Customizer map

Status: merged 2026-10-11 from the account `swell-wp/customizer` reference. Unverified against the current SWELL version (pass 2); panel names may have moved.

外観 → カスタマイズ

| Panel | Sections |
|---|---|
| サイト全体設定 | カラー設定 (メインカラー / アクセントカラー / テキスト / リンク / 背景) · フォント設定 (種類 / ベースサイズ / 行間) · レイアウト設定 (コンテンツ最大幅 / サイドバー幅) |
| ヘッダー設定 | PCヘッダー (ロゴ位置 / 高さ / 背景色 / ナビ位置) · SPヘッダー (スタイル / ハンバーガー色) · グローバルナビ (フォント / 色 / ホバー色) |
| フッター設定 | フッターウィジェット (カラム数 / 背景色) · フッタークレジット (コピーライト / 背景色) |
| トップページ | メインビジュアル (画像・スライダー) · コンテンツ (セクション表示) |
| 投稿・固定ページ | 記事一覧 (card / list / simple, カラム数) · 記事詳細 (アイキャッチ / サイドバー / 関連記事) |

## Handing over settings

List each one as a path and a value so a person can set it without guessing:

```
カスタマイズ → サイト全体設定 → カラー設定 → メインカラー: #1A56A0
カスタマイズ → サイト全体設定 → フォント設定 → 行間: 1.9
カスタマイズ → ヘッダー設定 → PCヘッダー → 高さ: 70px
```

Values come from the project's `DESIGN.md` (`../design/design-tokens.md`).
