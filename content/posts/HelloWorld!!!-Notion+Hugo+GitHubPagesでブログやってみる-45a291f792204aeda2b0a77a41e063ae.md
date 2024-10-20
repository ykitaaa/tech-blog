---
title: "HelloWorld!!! Notion+Hugo+GitHubPagesでブログやってみる"
date: "2024-09-22T11:13:00.000Z"
lastmod: "2024-10-20T15:15:00.000Z"
draft: false
hidden: false
series: []
nositemap: false
authors:
  - "YutaKita"
custom-front-matter: "hello"
tags:
  - "Hugo"
  - "GitHubActions"
categories:
  - "blog"
NOTION_METADATA:
  object: "page"
  id: "45a291f7-9220-4aed-a2b0-a77a41e063ae"
  created_time: "2024-09-22T11:13:00.000Z"
  last_edited_time: "2024-10-20T15:15:00.000Z"
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
      checkbox: false
    series:
      id: "B%3C%3FS"
      type: "multi_select"
      multi_select: []
    draft:
      id: "JiWU"
      type: "checkbox"
      checkbox: false
    nositemap:
      id: "JuyN"
      type: "checkbox"
      checkbox: false
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
      rich_text:
        - type: "text"
          text:
            content: "hello"
            link: null
          annotations:
            bold: false
            italic: false
            strikethrough: false
            underline: false
            code: false
            color: "default"
          plain_text: "hello"
          href: null
    tags:
      id: "jw%7CC"
      type: "multi_select"
      multi_select:
        - id: "e0f8d127-83e3-4cca-92c5-13d6c1e37803"
          name: "Hugo"
          color: "brown"
        - id: "3982b106-8807-4f6d-a55d-3313a183759b"
          name: "GitHubActions"
          color: "blue"
    categories:
      id: "nbY%3F"
      type: "multi_select"
      multi_select:
        - id: "8b6ab1fd-b670-4ecf-b083-a2ef3878f318"
          name: "blog"
          color: "default"
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
            content: "HelloWorld!!! Notion+Hugo+GitHubPagesでブログやってみる"
            link: null
          annotations:
            bold: false
            italic: false
            strikethrough: false
            underline: false
            code: false
            color: "default"
          plain_text: "HelloWorld!!! Notion+Hugo+GitHubPagesでブログやってみる"
          href: null
  url: "https://www.notion.so/HelloWorld-Notion-Hugo-GitHubPages-45a291f792204aed\
    a2b0a77a41e063ae"
  public_url: null
UPDATE_TIME: "2024-10-20T15:37:59.263Z"

---


# はじめに


はじめまして、ykitaaaと申します。  


以下サイトを参考にブログをとりあえず立ち上げてみました。  


[https://blog.code-del.com/posts/notion-hugoで寝転びながらブログを書く/](https://blog.code-del.com/posts/notion-hugo%E3%81%A7%E5%AF%9D%E8%BB%A2%E3%81%B3%E3%81%AA%E3%81%8C%E3%82%89%E3%83%96%E3%83%AD%E3%82%B0%E3%82%92%E6%9B%B8%E3%81%8F/)


⇒めんどくさがりの自分にぴったりでした！ありがとうございます！！  
　ブログタイトルがすばらしい。。。  


# ブログのシステム構成


## 構成

- Notion（のAPI）
	- メモアプリ⇒ここでブログを書きます
- Hugo
	- 静的HTML作成（Go言語なのでビルドが早い！！）
- GitHubPages
	- GitHubの静的HTMLのホスティングサービス

## デプロイまでの流れ

1. Notionで記事作成
1. GitHubActionsからNotionの記事取得（cron起動）
1. Notionの記事をMarkdownに変換
1. HugoでMarkdownからHTMLに変換
1. GitHubPagesにデプロイ

# メリット・デメリット


## メリット

- Notion
	- どこでも書ける
	- 慣れている人は書きやすい
	- 自分の技術メモを一つにまとめられる
- Hugo
	- 静的サイトなので早い
		- SEO的に良い
		GoogleのMatt Cuttsさんの動画↓  
		[https://youtu.be/-I4rWnQxxkM?si=HQwAxQ-DAv52PJeJ](https://youtu.be/-I4rWnQxxkM?si=HQwAxQ-DAv52PJeJ)  
		⇒ そこまで大きな要因ではないけど、速度は検索順位に影響しているみたい
		- 読者をイライラさせない（超大事）
	- テーマを使ってデザインを簡単に変更できる
- GitHubPages
	- ホスティングにお金がかからない（時間かかるけど）
	- SEO的には不安が残る

## デメリット

- Notion
	- Markdown記法の練習ができない笑
	- Notionのサービスが終わるか、API連携できなくなったらブログが書けない
		- NotionからMarkdownに変換したファイルを取れる手段を考えておく
- Hugo
	- WordPressに比べて若干SEOが不安
		- WordPressが老舗なのでおそらくノウハウが多い？
- GitHubPages
	- GitHubがサービス終了したら終わりだけど、おそらくは無いはず

# 少し困ったこと


GitHubActionsでエラーになり続けてて、なんでか見直してみたら、  


Notionのトークン名が誤って設定しているせいでNotionからデータ取得ができてませんでした。。。
トークン名は「NOTION_TOKEN」固定ですので、少しご注意を。。。  


手順は守りましょう！


[https://github.com/HEIGE-PCloud/Notion-Hugo?tab=readme-ov-file#setup-secrets-for-github-action](https://github.com/HEIGE-PCloud/Notion-Hugo?tab=readme-ov-file#setup-secrets-for-github-action)


# さいごに


どうなるか分からないですが、ちょっとずつ書いていきます～  


ブログのテーマも少しずついじったり、他の設定も触っていきます～

