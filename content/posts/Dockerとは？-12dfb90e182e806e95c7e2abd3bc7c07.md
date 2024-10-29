---
title: "Dockerとは？"
date: "2024-10-28T10:52:00.000Z"
lastmod: "2024-10-29T02:15:00.000Z"
draft: true
hidden: true
series: []
nositemap: true
authors:
  - "YutaKita"
tags: []
categories: []
NOTION_METADATA:
  object: "page"
  id: "12dfb90e-182e-806e-95c7-e2abd3bc7c07"
  created_time: "2024-10-28T10:52:00.000Z"
  last_edited_time: "2024-10-29T02:15:00.000Z"
  created_by:
    object: "user"
    id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
  last_edited_by:
    object: "user"
    id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
  cover: null
  icon: null
  parent:
    type: "database_id"
    database_id: "ffffb90e-182e-8161-8a7c-c191eda82682"
  archived: false
  in_trash: false
  properties:
    hidden:
      id: "%40%3Bf%3D"
      type: "checkbox"
      checkbox: true
    series:
      id: "B%3C%3FS"
      type: "multi_select"
      multi_select: []
    draft:
      id: "JiWU"
      type: "checkbox"
      checkbox: true
    nositemap:
      id: "JuyN"
      type: "checkbox"
      checkbox: true
    authors:
      id: "bK%3B%5B"
      type: "people"
      people:
        - object: "user"
          id: "11d54c62-5c86-4d27-a64b-4fdfb07609d7"
          name: "YutaKita"
          avatar_url: null
          type: "person"
          person:
            email: "tomamekuchi@gmail.com"
    custom-front-matter:
      id: "c~kA"
      type: "rich_text"
      rich_text: []
    tags:
      id: "jw%7CC"
      type: "multi_select"
      multi_select: []
    categories:
      id: "nbY%3F"
      type: "multi_select"
      multi_select: []
    summary:
      id: "x%3AlD"
      type: "rich_text"
      rich_text: []
    Name:
      id: "title"
      type: "title"
      title:
        - type: "text"
          text:
            content: "Dockerとは？"
            link: null
          annotations:
            bold: false
            italic: false
            strikethrough: false
            underline: false
            code: false
            color: "default"
          plain_text: "Dockerとは？"
          href: null
  url: "https://www.notion.so/Docker-12dfb90e182e806e95c7e2abd3bc7c07"
  public_url: null
UPDATE_TIME: "2024-10-29T09:22:03.710Z"

---


# 経緯


ひさびさにDockerを触ろうとしたらいろいろ忘れているので復習


# Dockerとは？

- コンテナ型仮想技術
	- ホスト型ではなく、コンテナ型
		- ホスト型：ホストOSの上にハイパーバイザーを通じてゲストOSを動か
			- メリット：マシンの完全コピー
			- デメリット：容量が大きい
			- 用語
				- ハイパーバイザー：コンピュータの仮想化技術（仮想マシンを作る）。例) VMWare
		- コンテナ型：ホストOSの上にDocker Engineを通じてコンテナを動かす
			- メリット①：OSカーネルを他のコンテナと共有  
			 　　　　　→ 利用リソースがホスト型に比べて少ない
			- メリット②：動作させるハードウェア環境に依存しない
- 設定ファイルで仮想環境が構築可能
	- メリット：プログラムの実行環境を共有できる
		- 設定ファイルを渡せば同じ環境が作れる
		- Docker Hubでも共有可能

# Dockerの構成


```mermaid
sequenceDiagram
    Client ->>DockerHost: docker run
    DockerHost->>Client
```


# Dockerの用語たち


## Docker Engine

- 

# aa


# Dockerの導入方法


# Dockerの設定ファイル


基本形を並べてみる


```Dockerfile
```


# Dockerの実行

- 起動中のコンテナ  
```bash
docker ps
```
- 起動  
新しいコンテナIDでコンテナを起動する  
```bash
# 通常起動
docker run -it [任意のコンテナID] 
# VOLUMEを紐づけてスタート
docker run -v ローカルディレクトリ:コンテナディレクトリ -it [コンテナID] 
```  
-i：インタラクティブモード＝標準入力が有効
-t：疑似TTY（Teletypewriterの疑似端末[電気信号で遠隔地との文字のやりとりをする]）を割り当てる
- 起動しているコンテナに対してコマンド実行
```bash
docker exec -it [コンテナID] [コマンド]
```
- 常時起動

# 派生

- Kubernetes  
コンテナ群の管理→スケーラビリティの確保
- Podman

# 参考


[https://www.docker.com/ja-jp/resources/what-container/](https://www.docker.com/ja-jp/resources/what-container/)


[https://docs.docker.jp/get-started/overview.html#docker-architecture](https://docs.docker.jp/get-started/overview.html#docker-architecture)


[https://docs.docker.jp/engine/index.html](https://docs.docker.jp/engine/index.html)

