---
title: "GitHubActionsでHugoのビルドファイルをコミットして草生やしてやる"
date: "2024-10-04T11:36:00.000Z"
lastmod: "2024-10-22T15:13:00.000Z"
draft: false
hidden: false
series: []
nositemap: true
authors:
  - "YutaKita"
tags:
  - "Hugo"
  - "GitHubActions"
categories:
  - "blog"
NOTION_METADATA:
  object: "page"
  id: "115fb90e-182e-80ba-a252-c525175fcc71"
  created_time: "2024-10-04T11:36:00.000Z"
  last_edited_time: "2024-10-22T15:13:00.000Z"
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
            content: "GitHubActionsでHugoのビルドファイルをコミットして草生やしてやる"
            link: null
          annotations:
            bold: false
            italic: false
            strikethrough: false
            underline: false
            code: false
            color: "default"
          plain_text: "GitHubActionsでHugoのビルドファイルをコミットして草生やしてやる"
          href: null
  url: "https://www.notion.so/GitHubActions-Hugo-115fb90e182e80baa252c525175fcc71"
  public_url: null
UPDATE_TIME: "2024-10-24T21:19:31.585Z"
EXPIRY_TIME: "2024-10-24T22:19:25.561Z"

---


# はじめに


## どんな人向け？

- Notionでブログ記事を書いて、GitHubActionからHugoを使ってビルドしている人  
　⇒[記事](/posts/helloworld-notion-hugo-githubpagesでブログやってみる)

## 問題


Notionでブログ記事を書いているとGitHubにコミットするわけではないので、  
GitHubの草が生えない。。。  
けど、Notionだとブログ記事を書きやすいから引き続き使いたい。


## 解決案

- ビルドしたブログ記事をGItHubAction中でGitHubにコミット
- コミット対象のブログ記事にはdraft状態（下書き状態）も含む  
→ モチベーション維持のため、下書きでもコミットしてGitHubの草生やしたい笑
- ただし、draft状態のブログ記事は非公開にしたい
→ Hugoのデフォルトだとdraft状態でも公開されてしまう

# STEP1. GitHubに自動コミットする


## 1. GitHubActionsのワークフロー設定


GitHubActionsのワークフローファイルで、  
Hugoのビルドが終わった後の処理に以下を追加する。  
本ブログ記事の設定は以下設定ファイルを参考にしてください。
[https://github.com/ykitaaa/tech-blog/blob/main/.github/workflows/cd.yml](https://github.com/ykitaaa/tech-blog/blob/main/.github/workflows/cd.yml)   


図1. ワークフローのyml


```yaml
      - name: Backup
        uses: stefanzweifel/git-auto-commit-action@v5
```


※ 注意：mainブランチにコミットしないと草生えないです  


## 2. コミット対象から画像ファイルを除外する


Notionから取得した画像のURLがAWS S3になっていて、  
毎回違うファイル名で取得される（？）ようなので、  とりあえず画像ファイルを除外する。  
以下の例はpublic配下のjpgおよびpngを除外する設定。  
試していないが、他のファイルも同じと思われる。  


図2. .gitignore


```xml
 public/*.jpg
 public/*.png
```


# STEP2. draft状態のブログ記事を隠す


プログ記事（posts）のMarkdownに以下設定の追加。  
たいていは、どのテーマであっても以下設定でRSSやsitemapからも隠せるので簡単にできる。  


  
図3. ブログ記事のMarkdown設定


```yaml
draft: true
hidden: true
nositemap: true
```


draft：ドラフト状態  
hidden：記事を隠す（一覧に出ないだけなので、直接遷移は可能）  
nositemap：sitemap.xmlから除外する（検索エンジンからの検索対策）  


  
Notionのページでhiddenプロパティを追加することで設定できる。  
Notionで新規記事を作る際に上記の設定がデフォルトになるように設定しておけば使いやすい。  


   
図4. Notion側のプロパティ（隠す場合）


![](https://prod-files-secure.s3.us-west-2.amazonaws.com/8763eeab-7a84-4eae-9d05-fda3364b0d6d/aa01cf7d-0124-4d08-bc9a-6c1b2535756e/image.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45GO43JXI4%2F20241024%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20241024T211925Z&X-Amz-Expires=3600&X-Amz-Signature=35fa3f120374c13ae12c6e8e2c5238ae23b742472af073db4d2016b343279694&X-Amz-SignedHeaders=host&x-id=GetObject)


# 参考URL


[https://zwbetz.com/discreet-drafts-in-hugo/](https://zwbetz.com/discreet-drafts-in-hugo/)

