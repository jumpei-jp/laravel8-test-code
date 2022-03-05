# Laravel8 test code
template file to create laravel env using docker  
Laravelの環境を作るためのDocker_template  
細かい操作のコメントも残していく

## Dockerfile
imageをdockerhub等から入手すると良いが、  
自分で作りたい場合にDockerfileを作成する。

## docker-compose
複数のコンテナを同時に立てる必要がある。  
その複数のコンテナを一元管理するのがdocker-compose

## 開発環境
* laravel: 8.x
* mysql: 8.0.26
* PHP: 8.0-apache-buster

## 手順
### ファイルの修正作業
1. docker/php/Dockerfile のプロジェクト名を修正
2. docker-compose.yamlのcontainer_nameを指定
3. .envファイルの修正

### コマンド操作

    docker-compose build
    docker-compose up

    #コンテナにログイン
    docker exec -it {コンテナ名} bash

    #Laravelのインストール（初期操作以外は必要無し）
    composer create-project laravel/laravel {プロジェクト名} "8.*"

    #このままだとアクセスできないので権限を変更
    chmod 777 -R storage/

## 各サービスログインコマンド

    php
    docker exec -it {コンテナ名} bash

    mysql
    docker exec -it {コンテナ名} mysql -u root -p