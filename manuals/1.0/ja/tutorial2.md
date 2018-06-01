---
layout: docs-ja
title: チュートリアル2
category: Manual
permalink: /manuals/1.0/ja/tutorial2.html
---
# チュートリアル

このチュートリアルは[チュートリアル](/manuals/1.0/ja/tutorial.html)とは違ったライブラリを使ってREST APIを作成して、そのAPIを使ったHTMLアプリケーションを作成します。
チュートリアルと被る箇所もありますが、おさらいのつもりでトライして見ましょう。

# プロジェクト作成

まずプロジェクトを作成します。

```bash
composer create-project bear/skeleton MyVendor.Ticket
```
**vendor**名を`MyVendor`に**project**名を`Ticket`として入力します。

次に依存するパッケージを一度にインストールします。

```bash
composer require  \
madapaja/twig-module \
koriym/now  \
bear/aura-router-module \
bear/api-doc  \
ray/query-module  \
ramsey/uuid  \
robmorgan/phinx
```

# マイグレーション

phinxで初期化を実行します。

```bash
cd var/db
mkdir -p db/migrations
mkdir -p db/seeds
../../vendor/bin/Phinx init
../../vendor/bin/Phinx create Ticket
```

`var/db/phinx.yml`の`development`を編集します。

```yaml
development:
    adapter: mysql
    host: localhost
    name: ticket
    user: root
    pass: ''
    port: 3306
    charset: utf8
```


## リソース

最初にアプリケーションリソースファイルを`src/Resource/App/Weekday.php`に作成します。
