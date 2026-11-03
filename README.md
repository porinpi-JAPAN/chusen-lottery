# 抽選まとめサイト（ポケカ＆ちいかわ）

ポケモンカード（ポケカ）の抽選販売情報と、ちいかわ関連の抽選・申込情報をまとめる静的サイト。
Cloudflare Pages にこのリポジトリを接続して公開する想定。

## 構成

- `index.html` — ページ本体。`data.json` を読み込んで一覧を描画する
- `data.json` — 抽選データ。ステータス（受付中／締切間近／開始前／終了）は閲覧時刻から自動判定する

## Cloudflare Pages の設定

- Framework preset: None
- Build command: なし（空欄）
- Build output directory: `/`

## データの更新方法

`data.json` の `items` を編集して push すると、Cloudflare Pages が自動で再デプロイする。

各 item の項目:

- `category`: `pokeca` または `chiikawa`
- `title`: 商品名・イベント名
- `shop`: 販売元・店舗
- `start` / `end`: 受付開始・締切（ISO 8601、+09:00）。不明な場合は `null`
- `method`: 応募方法・条件
- `url`: 応募ページのURL（未確認の場合は空文字）
- `note`: 補足
- `hot`: 注目アイテムなら `true`
- `applied`: 応募済みなら `true`
- `updatedAt`: データ全体の最終更新時刻
