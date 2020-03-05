docker-mirakurun-epgstation for DD Max M4
====

[Mirakurun](https://github.com/Chinachu/Mirakurun) + [EPGStation](https://github.com/l3tnun/EPGStation) の Docker コンテナ

## 前提条件

Docker, docker-compose の導入が必須

Digital Devices Max M4 + [DigitalDevices/dddvb](https://github.com/DigitalDevices/dddvb) の組み合わせを想定
当環境では [ppa:frodo-vdr/dddvb-0.9.37](https://launchpad.net/~frodo-vdr/+archive/ubuntu/dddvb-0.9.37) を使用

ホスト上の pcscd は停止する

## インストール手順

```
$ git clone https://github.com/ShinkoLab/docker-mirakurun-epgstation
$ cd docker-mirakurun-epgstation
$ sudo docker-compose pull
$ sudo docker-compose build

#チャンネル設定
$ vim mirakurun/conf/channels.yml

#コメントアウトされている restart や user の設定を適宜変更する
$ vim docker-compose.yml
```

## 起動

```
$ sudo docker-compose up -d
```
mirakurun の EPG 更新を待ってからブラウザで http://DockerHostIP:8888 へアクセスし動作を確認する

## 停止

```
$ sudo docker-compose down
```

## 設定

### Mirakurun

* ポート番号: 40772

### EPGStation

* ポート番号: 8888
* ポート番号: 8889

### 各種ファイル保存先

* 録画データ

```./recorded```

* サムネイル

```./epgstation/thumbnail```

* 予約情報と HLS 配信時の一時ファイル

```./epgstation/data```

* EPGStation 設定ファイル

```./epgstation/config```

* EPGStation のログ

```./epgstation/logs```
