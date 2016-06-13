IaC Study Room

# Docker で GitBucket

Mac, Win では [Docker Toolbox](https://www.docker.com/products/docker-toolbox) を使うと便利です。

以下の例では。

* docker コマンド
* docker-compose コマンド
* docker-machine コマンド

を使える前提です。

## イメージのビルド

docker-compose.yml のある docker ディレクトリに移動し、

```
$ docker-compose build
```

と実行します (手元の環境で 10 分弱かかりました)。

docker-machine で起動したゲスト OS 上で
Docker Engine のコンテナが稼働しています。
コンテナの EXPOSE は、ゲスト OS に forward されているので、
ゲスト OS の IP を調べ、EXPOSE した port へアクセスします。

```
$ docker-machine ls
NAME      ACTIVE   DRIVER       STATE     URL                         SWARM   DOCKER    ERRORS
default   *        virtualbox   Running   tcp://192.168.99.100:2376           v1.11.2
```

この場合、 http://192.168.99.100:8080 で Tomcat にアクセスできます。

## gitbucket サービスの実行

```
$ docker-compose run gitbucket
```

## あれがしたい！

### ビルド済みのイメージでシェルを起動したい。

```
$ docker run -it --rm local/openjdk8 /bin/bash
```

### 起動済みのコンテナに bash を起動する。

```
$ docker exec -it CONTAINER_ID /bin/bash
```

### docker-machine の IP を確認する。

```
$ docker-machine ls
```

URL 欄に表示されます。

### ビルド済みのイメージの一覧を確認する。


```
$ docker images
```
