# OkinawaDevOps3 
[2014-04-19 13:18]

## 今日やること
* 前回に引き続きLAMP環境のChefレシピ作成
 - Vagrant上ホストへKnifeでの遠隔インストールを目指す
 - 現状Apache分作成中

## 前回手を拱いたこと
* バージョン問題
 - chef,knifeのバージョン問題??
 - VirtualBoxのバージョンが低かった
* chef, knifeの設定が間違っていた

## 環境
* host OS : Mac OSX 10.9.2
* guest OS: CentOS 6.5
* Vagrant 1.3.5
* chef-solo 11.12.2
* knife-solo 0.3.0
* Vagrant sahara plugin

## やったこと
* Apacheインストールのレシピ作成

## 今回困ったこと
* ソースファイルを同梱したレシピの展開方法
 - cookbook_fileディレクティブ?
 - source指定、path(distination)指定する必要がある
* httpd: apr_sockaddr_info_get() failed for vagrant-centos65.vagrantup.com
 - ホスト名が解決できないエラーらしい。/etc/hostsに追加する。
```
    [vagrant@vagrant-centos65 ~]$ cat /etc/sysconfig/network
    NETWORKING=yes
    HOSTNAME=vagrant-centos65.vagrantup.com
    [vagrant@vagrant-centos65 ~]$ cat /etc/hosts
    127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
    ::1         localhost localhost.localdomain localhost6 localhost6.localdomain6
```
* httpd: Could not reliably determine the server's fully qualified domain name,
 - サーバーネームも/etc/sysconfig/networkのものに合わせる
* apacheが起動しない
 - 単純にコンフィグの記述ミス（syntax上の問題ではない)

## 課題
* デザインパターン。。という程ではないが見通しの良いレシピの書き方
* Vagrantとの連携（Vagrantの初期設定の設計や、ドメイン名やIPの割り当てについて
* レシピ検証方法の考案

