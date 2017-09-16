---
layout: post
title: "Hello World!"
date: 2017-09-16
description: "博客搭建过程"
tag: My Blog
---

## 题记
  纪念本博客的成立（满满的泪水T-T）

### 提前声明
  搭建博客主要是为了学习，也方便自己做笔记。<br>听朋友说github可以免费搭建，而且没有流量限制，也比较安全，所以就在这里安家了。<br>
  经过度娘的反复搜索，我发现大致使用的方法分为Hexo、Jekyll等，基本思路就是本地搭建然后上传到你的个人仓库中，本文对两种方法进行简单的介绍。

## 搭建前提
  一个Github账号是你必须拥有的（用我的平台还想不注册，给你一个眼神自行体会），下面我来介绍一下Github的注册姿势。打开官网[Github](https://github.com)就会出现你需要的注册页面Username，Email，Password。（记住自己的Username很重要！）<br>
  进入之后选择右上角 [Create a new repository](github.com/new),Repository name填上自己的名字yourname.github.io(yourname与你的注册用户名一致，这个就是你博客的域名了)例如，我的名字是Iewoaix8736，就填入Iewoaix8736.github.io。

# Hexo篇
  ~使用系统：windows 7 64位，编译器：sublime text3(第一次尝试使用的是windows系统，linux系统和mac系统搭建过程差不多，详细问度娘吧)

### 环境安装（node、git）
安装[Node.js](https://nodejs.org/en/download/)<br>
安装Git [Git官网](https://git-scm.com/downloads)(需要扶墙) [国内下载站](https://github.com/waylau/git-for-win)(Git for Windows)<br>
[Git食用教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/)这里推荐的廖雪峰老师的教程<br>
Git安装完成后，在开始菜单里找到“Git”->“Git Bash”，蹦出一个类似命令行窗口的东西，就说明Git安装成功！<br>
(记得配置Git环境变量)

安装完成后，还需要最后一步设置，在命令行输入：
```
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```
所有必备程序准备完成，可以开始安装Hexo了：
```
$ npm install -g hexo-cli
```
等待安装完成之后，所有环境就都准备完毕了。

### 本地配置博客
在电脑任意盘符下新建文件夹，并进入该目录按住Shift键点击鼠标右键选择"在此处打开命令窗口"，输入
```
hexo init blog
```
成功提示：
```
INFO  Start blogging with Hexo!
```
```
# 因为你初始化hexo 之后source目录下自带一篇hello world文章, 所以直接执行下方命令
$ hexo generate
# 启动本地服务器
$ hexo server
# 在浏览器输入 http://localhost:4000/就可以看见网页和模板了
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
访问http://localhost:4000/，便可以看到网站初步的模样

### 配置&&部署博客
重新打开CMD，输入：
```
ssh-keygen -t rsa -C "Github的注册邮箱地址"（引号中的内容替换为你的邮箱）
```
一路Enter，得到信息：
```
Your public key has been saved in /c/Users/user/.ssh/id_rsa.pub.
```
找到该文件后，用sublime打开,Ctrl+a(全选)复制左右内容，然后登录Github鼠标移动到右上角头像处下拉菜单中，点"setting"->"SSH and GPG keys"->"New SSH key":
```
Title：blog —— Key：输入刚才复制的—— Add SSH key
```

在本地blog目录下，用sublime打开_config.yml文件，修改参数信息
```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/
# Site #站点信息
title:  #标题
subtitle:  #副标题
description:  #站点描述，给搜索引擎看的
author:  #作者
email:  #电子邮箱
language: zh-CN #语言
# URL #链接格式
url:  #网址
root: / #根目录
permalink: :year/:month/:day/:title/ #文章的链接格式
tag_dir: tags #标签目录
archive_dir: archives #存档目录
category_dir: categories #分类目录
code_dir: downloads/code
permalink_defaults:
# Directory #目录
source_dir: source #源文件目录
public_dir: public #生成的网页文件目录
# Writing #写作
new_post_name: :title.md #新文章标题
default_layout: post #默认的模板，包括 post、page、photo、draft（文章、页面、照片、草稿）
titlecase: false #标题转换成大写
external_link: true #在新选项卡中打开连接
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
highlight: #语法高亮
  enable: true #是否启用
  line_number: true #显示行号
  tab_replace:
# Category & Tag #分类和标签
default_category: uncategorized #默认分类
category_map:
tag_map:
# Archives
2: 开启分页
1: 禁用分页
0: 全部禁用
archive: 2
category: 2
tag: 2
# Server #本地服务器
port: 4000 #端口号
server_ip: localhost #IP 地址
logger: false
logger_format: dev
# Date / Time format #日期时间格式
date_format: YYYY-MM-DD #参考http://momentjs.com/docs/#/displaying/format/
time_format: H:mm:ss
# Pagination #分页
per_page: 10 #每页文章数，设置成 0 禁用分页
pagination_dir: page
# Disqus #Disqus评论，替换为多说
disqus_shortname:
# Extensions #拓展插件
theme: landscape-plus #主题
exclude_generator:
plugins: #插件，例如生成 RSS 和站点地图的
- hexo-generator-feed
- hexo-generator-sitemap
# Deployment #部署，将 lmintlcx 改成用户名
deploy:
  type: git
  repo: 刚刚github创库地址.git
  branch: master
```
<b>注意，在每个参数的: 后都要加一个空格</b>

修改完毕后，进行发布：<br>
在 网站本地目录/blog 下执行：
```
$ hexo clean
$ hexo generate(简写 hexo g 同样执行)
$ hexo deploy
```
登录后就可以看到自己的博客了
### 发表文章
1.hexo new "创建文章"(引号中为自己文章的标题)<br>
2.Markdown语法编辑文章<br>
3.部署(所有打开CMD都是在blog目录下)
```
hexo clean #清除缓存 网页正常情况下可以忽略此条命令
hexo generate #生成
hexo server #启动服务预览，非必要，可本地浏览网页
hexo deploy #部署发布
```
如果在执行 hexo deploy 后,出现 error deployer not found:github 的错误，执行：
```
npm install hexo-deployer-git --save
```

# Jeklly篇
  使用hexo测试完成之后，我又听到朋友说起一种更加简便的方法进行博客搭建，于是又重新部署了一番。

### 博客部署
  注册一个github账号，我在这里遇到了很多坑，第一个要安装jeklly,安装完之后，导入其它人的博客，发现各种版本问题，各种版本不兼容。这里教给大家一个简答的方法，直接去[jekyll主题站](http://jekyllthemes.org/)找一个自己喜欢的主题，点进去之后，点"homepage"进入之后你会发现是一个github项目，然后直接点屏幕右上角的"forks".<br>
  这时候回到自己的github仓库，你会发现你拥有了一个一模一样的项目。进入项目后，点击项目的"Setting",将名字改成自己的用户名，格式：KamiSec.github.io<br>
  这时候，github就会自动为你分配一个博客域名,bsmali4.github.io。访问就会出现你的博客，和你fork过来的内容一模一样，包括文章内容和模版。这里只能是你的用户名＋github.io。默认一个用户只能有一个github博客，除非你充钱变强。(少年，想想吧，不充钱你会变强？)<br>
  看到自己艰难的用自己的github搭了一个别人的网站，想想是不是很气啊。没关系，可以让他变成自己的啊。(面包会有的，牛奶也会有的...)

 clone项目到本地 直接git clone你的项目到本地：
```
git clone https://github.com/KamiSec/KamiSec.github.io.git
```

把仓库克隆到本地，想怎么改还不是你说了算。进入项目目录，找到_config.yml,改成自己的内容，然后push上去就行了

### 更新文章
发布文章，固定命令走一套，网站更新没难度。
```
git init
git add .
git commit -m "change"
git remote add origin https://github.com/KamiSec/KamiSec.github.io.git
git push origin master
```

如果执行第四条命令出现fatal:remote origin already exists.说明分支已经存在，rm就行了
```
git remote rm origin
```
rm之后，再重新执行一下第四条命令，然后继续向下执行第五条就OK了。

windows版本中push时可能遇到如下错误
```
error: failed to push some refs to 'https://github.com/KamiSec/KamiSec.github.io
.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally. This is usually caused by another repository pushing
hint: to the same ref. You may want to first integrate the remote changes
hint: (e.g., 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```
解决方法：<br>
执行如下命令
```
git pull --rebase origin master
```
