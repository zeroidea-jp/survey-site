# survey-site

電波サイトサーベイ (導入前の電波環境調査) の公開サイトのソース。GitHub Pages で `https://survey.zeroidea.co.jp/` に公開する。whystop サイト (`zeroidea-jp/whystop-site`) の複製で、構成・テーマ・レイアウトは同じ。料金・連絡先は両サイトで同時に更新する。

- 生成: [Hugo](https://gohugo.io/) extended **0.167.0** (CI と同じ版。Blowfish v3.9.0 が対応を宣言している範囲 0.164〜0.167。`config/_default/hugo.toml` の `module.hugoVersion.min` 参照)
- テーマ: [Blowfish](https://github.com/nunocoracao/blowfish) v3.9.0 (`themes/blowfish`、git submodule)。トップは landing レイアウト。ヘッダーと冒頭は `layouts/partials/` で上書き
- ビルドと公開: `.github/workflows/hugo.yaml` (push to main → GitHub Actions → Pages)
- 外部 CDN・Web フォント・解析スクリプトは使わない

## ローカル確認

```bash
git clone --recurse-submodules git@github.com:zeroidea-jp/survey-site.git survey_site
cd survey_site
hugo server --port 1314   # http://localhost:1314/
```

## 編集する場所

| 何 | どこ |
|---|---|
| トップの文面 (冒頭、こんな時に、調査の内容、進め方、料金、よくある質問、問い合わせ) | `content/_index.md` (Markdown + Blowfish の shortcode) |
| 冒頭の見出し・リード・ボタン・図 | `content/_index.md` の front matter (`headline` / `heroLead` / `heroButtons` / `heroFigure`) |
| 報告書の見本 (PDF) | `static/files/survey_report_sample_v0.1.pdf` (正本は private repo `docs/templates/`) |
| メニュー | `config/_default/menus.ja.toml` |
| 色 (`colorScheme`: `assets/css/schemes/survey-*.css`)、ロゴ (`logoFile`)、Form の URL (`contactFormUrl`)、ヘッダー・フッター | `config/_default/params.toml` |
| 見た目の上書き | `assets/css/custom.css`、`layouts/partials/header/basic.html`、`layouts/partials/home/landing.html` |
| 図・ロゴ | `static/images/` |

## 権利

© 2026 株式会社ゼロアイデア (zeroidea)。サイトの文面・図・ロゴの無断転載・再利用はご遠慮ください。テーマ Blowfish は MIT ライセンス (`themes/blowfish/LICENSE`)。

## 書いてはいけないもの

顧客名・現場名・SSID/BSSID/IP/MAC・クレデンシャル・写真。報告書の見本は匿名化したものだけ。
