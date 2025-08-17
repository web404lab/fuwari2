---
title: 我的博客部署方案-近乎零成本
published: 2025-08-17
updated: 2025-08-17
description: '免费部署一个漂亮的博客'
tags: [Markdown, Blogging, astro,github action,github pages,fuwari]
category: 技术文章
draft: false
---
# 我的博客网站部署方案---astro+fuwari+github actions+github pages

> 本文截止2025年8月依旧有效

> 若出现莫名起来的错误，不必担忧，也许睡一觉起来就好了。~~我就是这样的，弄了一整天，第二天早上起来，就正常运行了。~~(文末附上我遇到的Bug，以及解决方案。)

## 第一步

找到fuwari的仓库，fork 默认分支

在你fork的仓库里删除原有的github workflowers文件

## 第二步

从astro官方文档里复制工作流文件
[astro文档](https://https://docs.astro.build/en/guides/deploy/github/)
将里面的action部署到你的仓库的action就行，无需更改代码。

## 第三步

我这里替大家踩过坑了。以下域名配置方案三选一

* [ ] 如果你打算使用username.github.io作为域名，就把仓库重命名为
  username.github.io
  然后在pages设置里面把页面源设置为github actions。
  更改仓库根目录下的`astro.config.mjs`
  找到以下两行代码位置并设置
  ```
  site: 'https://username.github.io',
  
  base: '/',
  ```
* [ ] 如果你打算使用username.github.io/repo-name作为域名，
  `astro.config.mjs`文件设置为

  ```
  site: 'https://username.github.io',
  base: '/repo-name',
  ```

文件内其余内容不变

pages设置与方案一的一致

* [ ] 如果你想用自定义域名。

`astro.config.mjs`文件设置为

  ```
  site: 'https://example.com',

  base: '/',
  ```

文件内其余内容不变

在域名DNS记录中添加记录，参见[github官方文档](https://https://docs.github.com/en/pages/getting-started-with-github-pages/securing-your-github-pages-site-with-https#verifying-the-dns-configuration)

github pages设置与方案一的一致

### OK，到这儿，你已经完成本教程了。

以下是我遇到的离谱Bug：

发布新文章时报错：

```
published: Expected type `"date"`, received `"string"`
```

我100%确定我没有问题，但就是不知道为什么会报错。

解决方案：睡一觉再试试

`(๑•̀ㅂ•́)و✧`
