# development-environment

## 環境  
Windows10 **Home**の利用者に限ります。しかも64bitしかダメです。
Windows10 Professional、Windows Serverの人は対象にしません。

理由は、Windows10 Pro、Serverは、Windows自身が備える仮想環境（Hyper-V）を使ってDockerが動くためです。しかし、Homeは、Hyper-Vが使えないです。

Windows10 Pro/Serverの利用者で、Dockerを導入したい方は、「windows10 pro docker」のGoogle検索で上位にでてくるので参照されるとよいのではないでしょうか？  

## Docker Toolboxの導入  
Hyper-Vが動かない**Home**では、Hyper-Vの代わりに**Oracle Virtual Box**を利用する、
[Docker Toolbox](https://docs.docker.com/toolbox/overview/)を利用します。  

インストールが完了すると、デスクトップ上に以下の3つのアイコンが作成されます。  
![aaa](https://camo.qiitausercontent.com/3fa3497d0d99d3c2245191c55ef99d5882c67a09/68747470733a2f2f71696974612d696d6167652d73746f72652e73332e616d617a6f6e6177732e636f6d2f302f3133333239312f63623636336266322d313731342d646665642d643863612d3937393338356130333764342e706e67)

## Docker Toolbox初期設定  
さきほどの3つのアイコンの「Docker Quickstart Terminal」を起動します。

ターミナルが開いて、初期設定が始まります。  
Dockerのクジラマークが表示されたら完了です。  
![aaa](https://camo.qiitausercontent.com/2a38bf59c733efa5b165a2846af633d61e27a376/68747470733a2f2f71696974612d696d6167652d73746f72652e73332e616d617a6f6e6177732e636f6d2f302f3133333239312f62616533396131652d353135342d346163382d663233332d6465666661623034666633632e706e67)

## 「MobaXterm」をインストール  
[ダウンロードURL](https://mobaxterm.mobatek.net/download-home-edition.html)  

## Dockerファイルをダウンロード  
[ダウンロードURL](https://github.com/k-kikuchi-ginga/development-environment/blob/master/dev/Dockerfile)  
任意のフォルダに配置する

## 「Dockerイメージ」devの作成  
Dockerファイルを配置したフォルダで下記コマンド実行  
```
docker build ./ -t dev
```

## 「Dockerコンテナ」の作成＆起動  
Dockerファイルを配置したフォルダで下記コマンド実行  
```
docker run -it -e DISPLAY=<ホストのIPアドレス>:0.0 dev
```

## 「STS」の起動
```
/usr/bin/sts-4.0.0.RELEASE/SpringToolSuite4 &
```
