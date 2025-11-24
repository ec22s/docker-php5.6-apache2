# docker-php5.6-apache2
forked from [alcalbg/docker-php5.6-apache](https://github.com/alcalbg/docker-php5.6-apache)

- 2025年11月、PHP5.6のWebアプリを動かす必要が出て作成しました

- 動作確認環境

  - macOS 15.6 (24G84)

  - GNU bash, version 5.3.3(1)-release (x86_64-apple-darwin23.6.0)

  - Docker version 29.0.0, build 3d4129b9ea

  - Docker Compose version 2.40.3

<br>

- 利用の便宜上、下記の更新をしました

  - `docker compose` と `make`の利用

    コンテナの数はfork元と同様1つです

  - コンテナ起動時に一部設定ファイルをホストからコピー

  - ドキュメントルートをホストと同期

  - ホストにマッピングするApache2のポートを `8888` に変更

<br>

- 使い方

  - `make up` でコンテナを起動します

  - `http://localhost:8888` で `phpinfo()` の結果が表示されます

    `DirectoryIndex` で `index.php` を `index.html` より優先にしています

  - `http://localhost:8888/index.html` で `Apache2 Debian Default Page` が表示されます

  - ホストの `doc-root` がコンテナの `/var/www/html` になっています

    任意の `.html` `.php` などソースを置きコンテナをリロードせずに開発できます

<br>

- Makeコマンド

  - コンテナのビルド＆起動 `make up`

    コンテナ名を `web` としています. 競合する場合は適宜変更して下さい

  - コンテナ終了 `make down`

  - コンテナ再起動 `make restart`

  - コンテナ再ビルド＆再起動 `make clean-restart`

  - コンテナにログイン `make in`

  - Apache2 ステータス確認 `make status` or `make apache-status`

  - Apache2 リロード `make apache-reload`

  - Apache2 強制リロード `make apache-force-reload`

<br>

以下、fork元のREADMEです

---

# docker-php5.6-apache
Docker image with old php 5.6 running on apache2 with usual php extensions:

- php5.6
- php5.6-bcmath
- php5.6-curl
- php5.6-gd
- php5.6-mcrypt
- php5.6-mbstring
- php5.6-mysql
- php5.6-sqlite3
- php5.6-soap
- php5.6-xml
- php5.6-zip
- php5.6-xdebug

Based on Debian stretch

# sample usage
`docker run -d -v /var/www/html:/var/www/html -p 8000:80 alcalbg/php5.6-apache`

visit http://localhost:8000/

