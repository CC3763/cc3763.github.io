---
layout: post
title: 记录本站建立的艰辛历程
date: 2024-04-10 10:39:25 +0800
last_modified_at: 2024-04-10 10:39:25 +0800
tags: [building website, Github Pages, jekyll]
toc:  true
---

![placeholder](/img/post/2024-04-10-the-building-journal-of-this-blog/screenshot%20v1.0.png "screenshot v1.0")
**摘要：** 本站为托管在Github Pages的个人博客，并利用Jekyll模板并生成的静态页面，目前该界面为初始界面，将在使用过程中不断优化、完善。

**关键词：** Blog; Github Pages; Jekyll

## 0 引言
建立本站的主要目的为记录一些在日常工作和学习中值得记录的过程和心得体会，由于博主本人并非科班出身，在建站的过程中难免出现很多磕绊，随着不断地学习和找寻各位大佬的教程，在不断解决bug的过程中终于使本站成功搭建并初具雏形。本文主要目的就是记录本站过程中的艰辛历程。

## 1 Git Pages[^3] #

### 1.1 创建Git Pages站点

本过程参考<a href="https://docs.github.com/zh/pages">Github文档</a>，此处不再赘述。
{: .message }

### 1.2 配置自定义域
1. 进入为站点创建的仓库；
2. 在顶部菜单栏找到Settings，如下图所示：
![placeholder](/img/post/2024-04-10-the-building-journal-of-this-blog/top-bar.png "top-bar")
3. 在侧边菜单栏找到Code and automation-Pages：
![placeholder](/img/post/2024-04-10-the-building-journal-of-this-blog/side-bar.png "side-bar")
4. 在页面底部找到Custom Domain
![placeholder](/img/post/2024-04-10-the-building-journal-of-this-blog/custom-domain.png "custom-domain")
在文本框中填入自己的域名，并点击save，待Github验证后将在仓库中自动创建CNAME文件，到此，Github内设置结束。

### 1.3 域名解析

此步骤参考<a href="https://docs.github.com/zh/pages">Github文档</a>在域名控制台完成设置。

## 2 Jekyll

Jekyll 是一个简单的博客形态的静态站点生产机器。它有一个模版目录，其中包含原始文本格式的文档，通过一个转换器（如 <a href="https://daringfireball.net/projects/markdown/">Markdown</a> ）和我们的 <a href="https://github.com/Shopify/liquid/wiki">Liquid</a> 渲染器转化成一个完整的可发布的静态网站，你可以发布在任何你喜爱的服务器上。Jekyll 也可以运行在 <a href="https://pages.github.com/">GitHub Page</a> 上，也就是说，你可以使用 GitHub 的服务来搭建你的项目页面、博客或者网站，而且是完全免费的。[^1]

### 2.1 安装Jekyll

虽然 Windows 并不是 Jekyll 官方支持的平台，但是也可以通过合适的方法使其运行在 Windows 平台上。[^2]
{: .message }

#### 2.1.1 环境准备
- Ruby 需要v2.5.0及以上版本，including all development headers（用 `ruby -v` 检查Ruby版本)
- RubyGems(用 `gem -v` 检查Gems版本)
- GCC 和 Make（用 `gcc -v`, `g++ -v`和 `make -v` 检查版本）

#### 2.1.2 安装Ruby和Jekyll
1. 从 <a href="https://rubyinstaller.org/downloads/">RubyInstaller Downloads</a> 下载一个 Ruby+Devkit 版本，并使用default options安装。<mark>注意：Ruby安装目录不能含有空格！</mark>
2. 在安装向导的最后一个阶段，执行 `ridk install` 步骤。这是安装具有本地扩展的 gems 所必需的。有关这方面的更多信息，您可以在 <a href="https://github.com/oneclick/rubyinstaller2#using-the-installer-on-a-target-system">RubyInstaller</a> 文档中找到。在选项中选择 `MSYS2 and MINGW development tool chain`。
**注：Ruby3.0.0以上不会再自带WebRick，需要手动添加到环境里面**
{: .message }
3. 打开命令提示符，使用 `gem install jekyll bundler` 安装Jekyll 和 Bundler。

### 2.2 选择一个主题
你可以在不同的主题库中查找和预览主题:
- <a href="https://github.com/topics/jekyll-theme">GitHub.com #jekyll-theme repos</a>
- <a href="https://jamstackthemes.dev/ssg/jekyll/">jamstackthemes.dev[^4]</a>
- <a href="http://jekyllthemes.org/">jekyllthemes.org</a>
- <a href="https://jekyllthemes.io/">jekyllthemes.io</a>
- <a href="https://jekyll-themes.com/">jekyll-themes.com</a>

### 2.3 使用主题
#### 2.3.1 克隆
找到意向主题的 web URL ，在本地目标文件夹中右键选择 Git Bash Here，使用以下命令克隆到本地：

```git clone <repository URL>```

#### 2.3.2 安装
因本站使用Github Pages托管，此处使用 <a href="">jekyll-remote-theme</a>将主题导入主分支：

1. 将 `gem 'jekyll-remote-theme'` 添加到 `Gemfile` 文件；
2. 将以下代码添加到 `_config.yml` 文件：

```
  plugins:
    - jekyll-remote-theme
    
  remote_theme:vszhub/not-pure-poole
```

#### 2.3.3 修改主题默认内容
使用自己的站点信息覆盖主题内容，以下为 Jekyll 网站的一般目录结构：


| 文件/目录 | 描述 |
| :-: | :- |
| `_config.yml` | 保存 <a href="https://jekyllcn.com/docs/configuration/">配置</a> 数据。很多配置选项都可以直接在命令行中进行设置，但是如果你把那些配置写在这儿，你就不用非要去记住那些命令了。 |
| `_drafts` | drafts（草稿）是未发布的文章。这些文件的格式中都没有 `title.MARKUP` 数据。学习如何 <a href="https://jekyllcn.com/docs/drafts/">使用草稿</a>。 |
| `_includes` | 你可以加载这些包含部分到你的布局或者文章中以方便重用。 |
| `_layouts` | layouts（布局）是包裹在文章外部的模板。布局可以在 <a href="https://jekyllcn.com/docs/frontmatter/">YAML 头信息</a> 中根据不同文章进行选择。 这将在下一个部分进行介绍。标签 `{{ content }}` 可以将content插入页面中。 |
| `_posts` | 这里放的就是你的文章了。文件格式很重要，必须要符合: `YEAR-MONTH-DAY-title.MARKUP`。 <a href="https://jekyllcn.com/docs/permalinks/">永久链接</a> 可以在文章中自己定制，但是数据和标记语言都是根据文件名来确定的。 |
| `_data` | 格式化好的网站数据应放在这里。jekyll 的引擎会自动加载在该目录下所有的 yaml 文件（后缀是 `.yml`, `.yaml`, `.json` 或者 `.csv` ）。这些文件可以经由 ｀site.data｀ 访问。如果有一个 `members.yml` 文件在该目录下，你就可以通过 `site.data.members` 获取该文件的内容。 |
| `_site` | 一旦 Jekyll 完成转换，就会将生成的页面放在这里（默认）。最好将这个目录放进你的 `.gitignore` 文件中。 |
| `.jekyll-metadata` | 该文件帮助 Jekyll 跟踪哪些文件从上次建立站点开始到现在没有被修改，哪些文件需要在下一次站点建立时重新生成。该文件不会被包含在生成的站点中。将它加入到你的 .gitignore 文件可能是一个好注意。 |
| `index.html` 和其他HTML、Markdown、Textile文件 | 如果这些文件中包含 <a href="https://jekyllcn.com/docs/frontmatter/">YAML 头信息</a> 部分，Jekyll 就会自动将它们进行转换。当然，其他的如 `.html`, `.markdown`, `.md`, 或者 `.textile` 等在你的站点根目录下或者不是以上提到的目录中的文件也会被转换。 |
| 其他文件/文件夹 | 其他一些未被提及的目录和文件如 `css` 还有 `images` 文件夹， `favicon.ico` 等文件都将被完全拷贝到生成的 site 中。这里有一些 <a href="https://jekyllcn.com/docs/sites/">使用 Jekyll 的站点</a>，如果你感兴趣就来看看吧。 |

*本表来源于<a href="https://jekyllcn.com/docs/structure/">https://jekyllcn.com/docs/structure/</a>*

#### 2.3.4 建立站点
1. 新建文件夹作为测试文件夹；
2. 在测试文件夹地址栏输入 `cmd` 命令在当前目录下打开命令提示符；
3. 使用以下命令建立站点
```
  jekyll build -s <source path> -d <destination path>
```
4. 使用 `bundle exec jekyll serve` 或 `jekyll serve` 生成预览站点，并在浏览器中输入生成的地址预览站点。
```
  D:\CC's Blog\myblog>jekyll serve
  Configuration file: none
              Source: D:/CC's Blog/myblog
        Destination: D:/CC's Blog/myblog/_site
  Incremental build: disabled. Enable with --incremental
        Generating...
                      done in 0.145 seconds.
  Auto-regeneration: enabled for 'D:/CC's Blog/myblog'
      Server address: http://127.0.0.1:4000
    Server running... press ctrl-c to stop.
  [2024-04-10 08:43:48] ERROR `/favicon.ico' not found.
```

## 3 Git推送
1. 将修改后的模板拷贝到站点本地文件夹内；
2. 在本地文件夹内右键选择 Git Bash Here;
3. 输入 `git status` 检查版本库状态；
4. 输入 `git add .` 将修改添加到暂存区；
5. 输入 `git commit - m 'commit'` 将暂存区内容添加到本地仓库中；
6. 输入 `git push` 将本地仓库内容推送到远程仓库

## 4 问题处理
1. 本片文章结束后，由于文中2.3.3的表格第四行中包含以下内容：
![placeholder](/img/post/2024-04-10-the-building-journal-of-this-blog/error1.png "error")
导致在 `jekyll build` 过程中报错，经检查，个人分析可能是由于 jekyll 运行机制，导致在 build 过程中寻找 `file.ext` 文件，以后需注意 Markdown 文件中尽量不要包含大括号内含百分号的形式。


**本博客主题选自 <a href="https://jamstackthemes.dev/ssg/jekyll/">Jamstack Themes</a> 中的 <a href="https://jamstackthemes.dev/theme/not-pure-poole/">not pure poole[^5]</a>**

## 参考：

[^1]: <a href="https://jekyllrb.com">Jekyll</a>

[^2]: <a href="https://jekyllcn.com/docs/windows/#installation">Windows 运行Jekyll</a>

[^3]: <a href="https://docs.github.com/zh/pages">GitHub Pages 文档</a>

[^4]: <a href="https://jamstackthemes.dev/ssg/jekyll/">Jekyll Themes</a>

[^5]: <a href="https://jamstackthemes.dev/theme/not-pure-poole/">Not Pure Poole</a>