---
layout: post
title: jekyll chirpy 配置及使用
date: 2024-12-04 07:12 +0800
description: 
image: 
category: 
tags: [jekyll]
published: true
math: true
author: tam
---

### 相关命令

- 在本地启动 jekyll：`bundle exec jekyll s`；
- 创建新文件：`bundle exec jekyll post "new post"`；
- 创建草稿：`bundle exec jekyll draft "new draft"`;

### 相关语法

```
> 显示 `tip` 类型提示的例子。
{: .prompt-tip }

> 显示 `info` 类型提示的例子。
{: .prompt-info }

> 显示 `warning` 类型提示的例子。
{: .prompt-warning }

> 显示 `danger` 类型提示的例子。
{: .prompt-danger }
```
> 显示 `tip` 类型提示的例子。
{: .prompt-tip }

> 显示 `info` 类型提示的例子。
{: .prompt-info }

> 显示 `warning` 类型提示的例子。
{: .prompt-warning }

> 显示 `danger` 类型提示的例子。
{: .prompt-danger }

### 相关网站

- [jekyll-compose（用于快速创建文章 ）](https://github.com/jekyll/jekyll-compose)
- [配置评论区](https://utteranc.es/?installation_id=57954315&setup_action=install)

### 安装 docker desktop，下载 jekyll 镜像，fork chirpy 项目。

### 修改头像样式：

  ```css
  /* 修改头像背景颜色 */
  /workspaces/jekyll/SharkTam.github.io/assets/css/jekyll-theme-chirpy.scss
  .rounded-circle {
    border-radius: 50% !important;
    background-color: white;
  }
  
  /workspaces/jekyll/SharkTam.github.io/_includes/sidebar.html
  <a href="/" id="avatar" class="rounded-circle">
        <!-- 省略会被Jekyll读取的一些代码 -->
          <img src="" width="150px" height="150px" alt="avatar" onerror="this.style.display='none'">
        <!-- 省略会被Jekyll读取的一些代码 -->
  </a>
  
  /* 修改头像大小 */
  /workspaces/jekyll/SharkTam.github.io/_sass/layout/_sidebar.scss
  #avatar {
      display: block;
      width: 8rem;
      height: 8rem;
      overflow: hidden;
      box-shadow: var(--avatar-border-color) 0 0 0 2px;
      transform: translateZ(0); /* fixed the zoom in Safari */
  
      @include bp.sm {
        width: 9rem;
        height: 9rem;
      }
  
      img {
        transition: transform 0.5s;
  
        &:hover {
          transform: scale(1.2);
        }
      }
  }
  ```

### [修改网页 favicons](https://pansong291.github.io/chirpy-demo-zhCN/posts/customize-the-favicon/)

### 配置 jekyll compose

  Add this line to your application's Gemfile:

  ```
  gem 'jekyll-compose', group: [:jekyll_plugins]
  ```

  And then execute:

  ```
  $ bundle
  ```

  After you have installed (see above), run `bundle exec jekyll help` and you should see. Listed in help you will see new commands available to you:

  ```
  draft      # Creates a new draft post with the given NAME
  post       # Creates a new post with the given NAME
  publish    # Moves a draft into the _posts directory and sets the date
  unpublish  # Moves a post back into the _drafts directory
  page       # Creates a new page with the given NAME
  rename     # Moves a draft to a given NAME and sets the title
  compose    # Creates a new file with the given NAME
  ```

  To customize the default plugin configuration edit the `jekyll_compose` section within your jekyll config file.

  **auto-open new drafts or posts in your editor**: 

  ```
  jekyll_compose:
  	auto_open: true
  ```

  and make sure that you have `EDITOR`, `VISUAL` or `JEKYLL_EDITOR` environment variable set. For instance if you wish to open newly created Jekyll posts and drafts in Atom editor you can add the following line in your shell configuration:

  ```
  export JEKYLL_EDITOR=atom
  ```

  `JEKYLL_EDITOR` will override default `EDITOR` or `VISUAL` value. `VISUAL`  will override default `EDITOR` value.

  > 将上述的环境变量添加到 `~/.zshrc` 中，然后 `zsh ~/.zshrc`，`vscode` 将上面的 `atom` 改为 `code` 即可

  **Set default front matter for drafts and posts**: 见官方文档

### author 信息配置

帖子的作者信息通常不需要在 头信息 中填写，默认情况下会从配置文件中 social.name 变量和 social.links 的第一个条目中获取。但您也可以按如下方式覆盖它：

在 `_data/authors.yml` 中添加作者信息（如果您的网站没有此文件，请立即创建一个）。
```
<author_id>:
  name: <full name>
  twitter: <twitter_of_author>
  url: <homepage_of_author>
```

然后用 `author` 指定单个条目或用 `authors` 指定多个条目：
```
---
author: <author_id>                     # 针对单个作者
# or
authors: [<author1_id>, <author2_id>]   # 针对多个作者
---
```
>从 _data/authors.yml 文件中读取作者信息的好处是页面将具有 twitter:creator 元标记，这丰富了 Twitter Cards ，并且有利于 SEO 。

### vscode 粘贴图片配置

`VSCode 1.79` 更新，支持 `Markdown` 中直接粘贴图片！配置方法：

`ctrl ,` 打开 vscode 的设置界面，搜索 `copyfile`，修改 `Markdown > Copy Files:Destination`

|item|value|function|
|---|---|---|
|`SharkTam.github.io/_posts/*`|`../assets/img/article/${fileName}`| 对 `SharkTam.github.io/_posts/` <br> 下的文件进行图片粘贴时，图片存储到<br>  `SharkTam.github.io/assets/img/article/`<br>  目录下|
|`**/*`|`${documentDirName}/imgs/${fileName}`|在对任一目录的文件进行图片粘贴时，<br> 在当前文件的同级目录下创建 `imgs` <br> 文件夹并将图片放到 `imgs` 文件夹中|

![alt text](../assets/img/article/PixPin_2024-11-29_21-07-37.png)
