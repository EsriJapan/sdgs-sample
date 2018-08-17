# sdg-dash

SDGs に関連するデータやサービスを検索するためのプロトタイプ Web アプリケーションです。

EmberCLI を利用して作成されたダッシュボード スタイルのアプリケーションです。セットアップや Ember についての詳細は以下を参照ください。

[View it Live（英語）](http://esri.github.io/sdg-dash/)

※ このリポジトリは Esri の [sdg-dash](https://github.com/Esri/sdg-dash) を日本語にしたものです。  
アプリケーションで使用している目標を表す画像は [JAPAN SDGs Action Platform（出典：外務省ホームページ）](https://www.mofa.go.jp/mofaj/gaiko/oda/sdgs/index.html)から取得しました。

## API のセットアップ

![SDG APIs Overview](https://s3.amazonaws.com/sdg-dash-misc/sdg-apis-overview.jpg)

アプリケーションは 2 つの API により動作します。ひとつめは、SDGs に関連するすべてのメタデータを含んだ [SDG API](https://github.com/Esri/sdg-api) です。ふたつめは、[Sample SDG Dashboards API](https://github.com/apfister/sdg-dashboard-api/) です。これは、指定した地域のダッシュボードにカード形式のレイアウトを定義する JSON データを提供するサンプル API です。Sample SDG Dashboards API は、今後廃止され、[ArcGIS Open Data](http://opendata.arcgis.com/about) へステーブルなフレームワークが作成される予定です。

各 API をセットアップし、実行したら、`config/environment.js` で `sdgApi` および `sdgDashboardsApi` のインスタンスの値を独自にホストした API へそれぞれ変更します。

例：

```javascript
module.exports = function(environment) {
  var ENV = {
    modulePrefix: 'sdg-dash',
    environment: environment,
    baseURL: '/',
    locationType: 'auto',
    EmberENV: {
      FEATURES: {
        // Here you can enable experimental features on an ember canary build
        // e.g. 'with-controller': true
      }
    },

    sdgApi: 'http://localhost:3000/',
    sdgDashboardsApi: 'http://localhost:3100/'

  };
```

## セットアップおよびローカルで実行するための前提条件

以下をインストールしておく必要があります。

- [Git](http://git-scm.com/)
- [Node.js](http://nodejs.org/) (with NPM)
- [Bower](http://bower.io/)
- [Ember CLI](http://www.ember-cli.com/)
- [PhantomJS](http://phantomjs.org/)

## インストール

- `git clone <repository-url>` 
- クローンしたリポジトリのディレクトリへ移動
- `npm install`
- `bower install`

## 実行 / 開発

- `ember server`
- [http://localhost:4200](http://localhost:4200) へアクセス

### コード ジェネレーター

コードを生成するためのジェネレーターを活用できます。詳細は、`ember help generate` をお試しください。

### テスト

- `ember test`
- `ember test --server`

### ビルド

- `ember build` (development)
- `ember build --environment production` (production)

### デプロイ

アプリをデプロイするために必要なものを設定します。

## 関連リンク

- [ember.js](http://emberjs.com/)
- [ember-cli](http://www.ember-cli.com/)
- ブラウザーの開発ツール エクステンション
    - [ember inspector for chrome](https://chrome.google.com/webstore/detail/ember-inspector/bmdblncegkenkacieihfhpjfppoconhi)
    - [ember inspector for firefox](https://addons.mozilla.org/en-US/firefox/addon/ember-inspector/)

## ライセンス

Copyright 2016 Esri

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

A copy of the license is available in the repository's [LICENSE](/LICENSE) file.

[](Esri Tags: ArcGIS Web Mapping SDG Dashboard Ember OpenData)
[](Esri Language: JavaScript)