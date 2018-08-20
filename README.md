# 持続可能な開発目標（SDGs）に関するサンプル プロジェクト

Esri が提供する SDGs に関連する以下のプロジェクトを日本語にし、集約しました。
- [sdg-dash](https://github.com/Esri/sdg-dash)
  - sdg-api と sdg-dashboard-api を使用して、SDGs の各指標に関連する情報を地域ごとに地図に可視化するダッシュボード アプリケーションです。
  - [sdg-dash（日本語）](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-dash) は、アプリケーションに日本語のロケール ファイルを追加しています。
- [sdg-api](https://github.com/Esri/sdg-api)
  - SDGs のメタデータを配信する API です。
  - [sdg-api（日本語）](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-api) は、メタデータを日本語に変更しています。
- [sdg-dashboard-api](https://github.com/apfister/sdg-dashboard-api/)
  - ダッシュボードのレイアウトやデータソースを定義した JSON を配信する API です。
  - [sdg-dashboard-api（日本語）](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-dashboard-api) は、日本のサンプル データを表示するよう定義した JSON を配信します。

# 使い方

1. リポジトリをクローンします。
2. ダッシュボード アプリケーション（[sdg-dash](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-dash)）をインストールします。
3. SDG API（[sdg-api](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-api)）およびダッシュボード API（[sdg-dashboard-api](https://github.com/EsriJapan/sdgs-sample/tree/master/sdg-dashboard-api)）をインストールします。

※ インストール方法は各プロジェクトの README を参照してください。

## 独自データの使用

ダッシュボード アプリケーションで地域ごとに表示されるマップやチャートなどのコンポーネントをどのようにレイアウトするかは、ダッシュボード API（sdg-dashboard-api）により定義されます。  
サンプルのダッシュボード API は、都道府県ごとに年収 300 万円未満の世帯の割合を表示するレイアウトを配信しています。  
以下の手順でダッシュボード API を変更することで、アプリケーションに独自のデータを表示できます。

### 1. 地域の設定

`sdg-dashboard-api\data\geographies.json` にダッシュボードに表示する地域を設定します。

以下のオプションに値を設定します。
- `id`：一意の ID
- `display`：ダッシュボードに表示する地域の名称
- `geo_group`：地域のグループ（`countries` または `cities`）

### 2. レイアウトの設定

`sdg-dashboard-api\data\dashboards.json`（`countries` グループ）または `sdg-dashboard-api\data\dashboards-cities.json`（`cities` グループ）に選択した地域に表示するダッシュボードのレイアウトを定義します。

まず、地域を指定します。`country_code` に `geographies.json` の `id` とマッチする ID を設定します。
続いて、指定した地域のどの指標でレイアウトを使用するのか指標のインデックスを指定します。
そして `items` に使用するコンポーネントの表示位置や大きさとコンポーネントの設定を渡します。

ダッシュボード アプリケーションは [Bootstrap](https://getbootstrap.com/) を使用しており、表示位置もグリッド システムがベースになっています。そのため、アプリケーションで表示できるカラム数は 12 です。

以下は、現在、確認できているコンポーネントです。
- `"map-card"`：Web マップを表示します。
- `"storymap-card"`：ストーリーマップのサムネイルを表示し、クリックでストーリーマップを開きます。
- `"summary-stat-card"`：ArcGIS Web サービスの統計クエリを使用して、サービスに含まれる数値情報の合計や平均の値を表示します。
- `"chart-card"`：[cedar.js](https://esri.github.io/cedar/) を使用して、チャートを表示します。

各オプションの設定方法はサンプルの `dashboards.json` およびダッシュボード アプリケーションのコンポーネント ファイルを参照してください。

## 指標のローカライズ

ダッシュボード アプリケーションで表示される SDGs の指標は SDG API（sdg-api）が配信するメタデータを使用しています。  
メタデータを日本語化するにあたり、[持続可能な開発目標（SDGs）（出典：総務省ホームページ）](http://www.soumu.go.jp/toukei_toukatsu/index/kokusai/02toukatsu01_04000212.html) を使用し、翻訳されていない情報に関しては原文のまま提供しています。  
翻訳の修正や日本に合わせた指標を使用したい場合などは、以下のファイルを変更してください。
- `sdg-api\data\goals-final-ja.json`
- `sdg-api\data\indicators-final.json`
- `sdg-api\data\targets-final.json`