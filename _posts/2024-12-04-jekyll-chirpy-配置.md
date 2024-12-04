---
layout: post
title: jekyll chirpy 配置
date: 2024-12-04 07:12 +0800
description: 
image: 
category: 
tags: [jekyll]
published: true
math: true
---

- [x] 安装 docker desktop，下载 jekyll 镜像，fork chirpy 项目。

- [x] 修改头像样式：

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

- [ ] 修改网页 favicons

- [ ] 配置 jekyll compose

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