# Docker_LAMP environment for learning
## Dockerで構築した学習用のLAMP環境
### 構築される環境
```
webサーバー : CentOS7.6
dbサーバー: MySQL 5.7
```
### USAGE
- 前提条件
  * DokcerがPCにインストールされており、docker-composeコマンドが使用できる様になっていること。※確認`docker-compose --version`
  * docker for Macで動作確認済

#### Lamp環境の構築と実行
1.webサーバーとDBサーバーのコンテナを実行
```
$ cd Lamp_env # <= docker-compose.ymlのディレクトリに移動
$ docker-compose up -d
```
2. 正常に実行されているか確認(一例)
  - webサーバー
    - ブラウザで`127.0.0.1`もしくは`localhost`を開き、PHPのバージョン情報一覧が表示されればOK

  - webサーバー・DBサーバー共通
`docker ps`コマンドを実行し*lamp_env_web*と*lamp_env_db*のコンテナが存在し、STATUS項目がUpになっていること
```
$ docker ps
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                               NAMES
5af45db97332        lamp_env_web        "/usr/sbin/httpd -DF…"   27 minutes ago      Up 27 minutes       0.0.0.0:80->80/tcp                  web_server
50bac802ded7        lamp_env_db         "docker-entrypoint.s…"   27 minutes ago      Up 27 minutes       0.0.0.0:3306->3306/tcp, 33060/tcp   mysql_server
```