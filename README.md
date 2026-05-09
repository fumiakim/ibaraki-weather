# 雨雲ナウキャスト & 7日間天気予報

気象庁 (JMA) のオープンデータを直接利用した、地点切替可能な雨雲ナウキャスト＋7日間天気予報＋当日気温推移ビューアー。
単一 HTML（ビルド不要、依存は CDN の Leaflet のみ）。

## 機能

- **雨雲ナウキャスト**: 高解像度降水ナウキャスト (`hrpns`) を地理院淡色地図に重ね、過去1時間〜1時間先までを5分刻みでスライダー＋自動再生。
- **地点切替**: つくば／柳津（福島県会津）／姫路／名古屋 をワンクリックで切替。マーカークリックでも可。
- **7日間天気予報**: 選択地点の都道府県の予報（細分・気温観測点も自動連動）。3日先までは6時間ごとの降水確率、4日目以降は週間予報＋信頼度。
- **当日の気温推移**: 最寄りのアメダス観測点から10分値を取得し SVG 折れ線で表示。
- **自動更新**: 雨雲5分／気温10分／予報30分。

## 使い方

`index.html` をブラウザで開くだけ。ローカルサーバ等は不要。

```bash
open index.html       # macOS
```

GitHub Pages にデプロイ済みの場合はそのまま URL でアクセス可能。

## データ出典

すべて気象庁 (Japan Meteorological Agency) のオープンエンドポイントから直接取得しています。

| 種類 | エンドポイント |
| --- | --- |
| ナウキャスト時刻一覧 | `https://www.jma.go.jp/bosai/jmatile/data/nowc/targetTimes_N1.json`, `_N2.json` |
| ナウキャストタイル | `https://www.jma.go.jp/bosai/jmatile/data/nowc/{basetime}/none/{validtime}/surf/hrpns/{z}/{x}/{y}.png` |
| 天気予報 | `https://www.jma.go.jp/bosai/forecast/data/forecast/{officeCode}.json` |
| 天気アイコン | `https://www.jma.go.jp/bosai/forecast/img/{code}.svg` |
| アメダス観測点表 | `https://www.jma.go.jp/bosai/amedas/const/amedastable.json` |
| アメダス10分値 | `https://www.jma.go.jp/bosai/amedas/data/point/{code}/{YYYYMMDD}_{HH}.json` |

ベース地図は[国土地理院タイル（淡色地図）](https://maps.gsi.go.jp/development/ichiran.html)を利用しています。

## 注意

- 気象庁の[利用規約](https://www.jma.go.jp/jma/kishou/info/coment.html)に従ってください（出典明示・過度なアクセス禁止）。
- 本リポジトリは個人用途・学習目的の試作品で、気象庁公式とは無関係です。
