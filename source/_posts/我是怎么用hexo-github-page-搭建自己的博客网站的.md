---
uuid: 79e9f160-1b6f-11f0-a8a6-a707e1d81c15
title: 我是怎么用hexo+github page 搭建自己的博客网站的
abbrlink: 56132
date: 2025-04-17 17:36:44
tags:
categories:
- 学习记录
---
# 记录一下我的博客搭建过程
<!-- vscode-markdown-toc -->
* 1. [前言](#)
* 2. [框架及工具：github page，hexo，cloudflare](#githubpagehexocloudflare)
	* 2.1. [前端框架：___hexo___](#___hexo___)
	* 2.2. [静态网站托管：github page](#githubpage)
	* 2.3. [免费的CDN加速站点：cloudflare](#CDNcloudflare)
* 3. [部署前的准备](#-1)
	* 3.1. [安装npm与git](#npmgit)
		* 3.1.1. [由于这些东西都比较简单 我直接一笔带过](#-1)
* 4. [安装hexo 并初始化hexo项目](#hexohexo)
	* 4.1. [安装hexo](#hexo)
	* 4.2. [初始化hexo项目](#hexo-1)
	* 4.3. [本地部署hexo项目](#hexo-1)
	* 4.4. [在浏览器中访问个人网站](#-1)
* 5. [配置github pages](#githubpages)
	* 5.1. [创建github账户](#github)
	* 5.2. [创建仓库并部署代码](#-1)
* 6. [购买域名并使用cloudflare代理加速。](#cloudflare)
	* 6.1. [购买域名](#-1)
	* 6.2. [替换你的域名](#-1)
* 7. [使用cloudflare做cdn加速。](#cloudflarecdn)
	* 7.1. [打开cloudflare注册并登录](#cloudflare-1)
	* 7.2. [将自己的域名交给cloudflare管理](#cloudflare-1)
	* 7.3. [将自己域名的DNS服务器改为cloudflare](#DNScloudflare)
	* 7.4. [通过cloudflare添加DNS记录，使域名指向github ip，以便加速生成。](#cloudflareDNSgithubip)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->
##  1. <a name=''></a>前言

>这是我创建我的博客网站以来的第一篇文章，本来走的方向就是后端对网页的建立一窍不通，之前也偷了很多懒对于计算机网络的东西也是没有了解多少，所以折腾了四五天，碰了不少壁，但网站部署出来的那一刻，是我接触代码以来最有成就感感觉自己做的事最有意义的一个瞬间。

>那么这篇文章，我就来将我搭建博客网站的过程以及工具和框架分享给大家，哪怕大家没有接触过编程，也可以按照我下面的步骤一步一步搭建出属于自己的博客。

>我会省略页面开发，美化的过程，只单纯的向大家展示如何部署。


##  2. <a name='githubpagehexocloudflare'></a>框架及工具：github page，hexo，cloudflare
###  2.1. <a name='___hexo___'></a>前端框架：___hexo___
hexo是一款非常简洁又高效的博客框架，哪怕你没有接触过前端的知识，你也可以通过套框架开发你个人的博客项目。你只需要跟着教程输几个指令就可以完成个人博客的开发。
###  2.2. <a name='githubpage'></a>静态网站托管：github page

如果你想运行自己的前端项目，那么肯定需要一台服务器，但是只是为了自己搭建一个博客，又不是什么大型的项目，所以犯不着花那个钱再去买一个云服务器。  

这里，我们就要用到github page了，github page可以免费托管你的静态网页，这样能最大的节省成本。


###  2.3. <a name='CDNcloudflare'></a>免费的CDN加速站点：cloudflare
>由于国情存在一堵墙，所以我们对github的访问是极其的慢的，甚至有时候直接访问不到。


>因此为了保证其他人或者我们自己对我们博客访问连接速度，我们就要用到CDN加速服务。


cloudflare每天会提供十万次点击的免费次数，虽然站点不在国内，但也比直接连接github快很多。

##  3. <a name='-1'></a>部署前的准备
###  3.1. <a name='npmgit'></a>安装npm与git
####  3.1.1. <a name='-1'></a>由于这些东西都比较简单 我直接一笔带过
##### git的安装

  
    
        
git官方下载地址: Git - Downloading Package (git-scm.com)

安装后验证: 在 cmd 中输入命令 `git --version`, 查看 Git 版本


##### npm的安装
官方下载地址: Node.js (nodejs.org)


安装后验证：cmd中输入`node -v`, 查看 Node 版本

##  4. <a name='hexohexo'></a>安装hexo 并初始化hexo项目
确保你的电脑上有 npm 以及 git，就可以开始安装hexo并本地初始化项目了。
###  4.1. <a name='hexo'></a>安装hexo
打开命令行 输入 `npm install -g hexo-cli`

这是全局安装hexo的命令，这样你就可以在任何一个地方使用hexo的命令了。

同样的 安装结束后 输入 `hexo -v` 验证是否安装成功。
###  4.2. <a name='hexo-1'></a>初始化hexo项目

可以新建一个文件夹，随便什么名字，可以写成MyBlog。

打开你新建的这个文件夹，在文件夹中运行命令行，可以这样：
<br><br><br><br>

![alt text](image-2.png)
<br><br><br>

接着输入 `hexo init` 项目就会初始化。
<br><br><br>
![alt text](image-3.png)

完成后如下：
<br><br>
![alt text](image-4.png)
<br><br><br><br>
文件夹如下：
<br><br><br><br>
![alt text](image-5.png)

###  4.3. <a name='hexo-1'></a>本地部署hexo项目

接下来开始部署在本地上，输入`hexo generate` 或 `hexo g`来生成静态文件。

如下：


![alt text](image-6.png)

本地部署指令：`hexo server`或`hexo s`

![alt text](image-7.png)
<br><br>
出现以上内容，说明启动成功，访问localhost:4000 端口，就可以看到刚刚部署的网页了。
<br><br>

###  4.4. <a name='-1'></a>在浏览器中访问个人网站

在浏览器中输入 localhost:4000

将出现如下页面：

![alt text](image-8.png)

我们可以在博客文件夹中的___config.yml__文件中修改配置，如title，subtitle，时区，语言等，大家可以自行探索，或查看官方文档，这里还是比较简单。

##  5. <a name='githubpages'></a>配置github pages

###  5.1. <a name='github'></a>创建github账户
>考虑到很多就算是计算机专业的同学可能都不知道github是什么，这一部分我会尽量写详细点，假定你是个连github都不会连的小白。

https://gitee.com/rmbgame/SteamTools/releases/tag/3.0.0-rc.16

首先我们打开这个网站 下载曾经的steam++，现在的watt toolkit。

这个软件集成了steam，github的加速，让大家可以不用加速器或者挂梯子就能访问github，里面还配置了其他站点的加速，有兴趣的可以自己探索。

现在我们打开github并创建一个账户

https://github.com

>注册这一步就不再细说，补充一点，用户名可以好好起一个自己喜欢的，因为我们要访问自己的github page是通过 “用户名”.github.io来访问的，不过也无所谓，后期我们会购买一个新的域名做cdn加速，当然如果你能忍受国内链接github这个超慢的速度，也可以不用再做域名映射。

###  5.2. <a name='-1'></a>创建仓库并部署代码

接着我们创建一个仓库，点击左上角的new：

![alt text](image-9.png)

__注意！这里的仓库名一定要是你的 <用户名>.github.io，否则github不会给你做页面托管！__


![alt text](image-11.png)

<br><br>
接下来我们进入到仓库，并复制对应的github链接：


![alt text](image-12.png)


打开hexo文件中的_config.yml文件

拉到最下面，找到deploy

![alt text](image-13.png)

repo中输入的是你的仓库地址。

__注意：__ yml格式的文件，对应低一级的字段要在上级字段前至少空两格

我们在从博客文件夹中打开命令行，输入以下指令：

`npm install hexo-deployer-git --save`

该指令是安装hexo部署git的插件。

然后我们输入 `hexo deploy` 或 `hexo d`

就可以将个人项目部署在github page上了。

接着我们直接访问 <你的用户名>.github.io 就可以访问到我们部署的博客了。

同样的，其他人访问该链接也是如此。

___最麻烦的东西就在下面了，如果你觉得配置到github上已经足够，看到这里就可以了___
<br><br>
___但是如果你想搭起一个国内能够较为稳定访问的网站，那就接着往下看___
-----------------------------------

##  6. <a name='cloudflare'></a>购买域名并使用cloudflare代理加速。

###  6.1. <a name='-1'></a>购买域名

上述的一切都做好之后，就可以上网购买一个域名了，域名购买网站极多并且优惠服务隔三差五的就会有，我不去细讲有哪些域名购买服务网站。我这里只简单说一下我是在哪买的。

阿里云有一个新用户首年优惠，超级便宜，大家可以看看后续一年价格少的选，到期也可以在考虑续费还是购买新的域名，这里我就不再赘述。
![alt text](image14.png)

###  6.2. <a name='-1'></a>替换你的域名

点进你的page仓库，点击settings
![alt text](image-15.png)

点击左侧的page

![alt text](image-16.png)

在custom domain这一栏填入你的域名并save

>只要填入save即可，大多数时候会显示dns解析有错，不用理会，依旧可以通过域名访问。

![alt text](image-17.png)

>注意，每次用hexo deploy的时候这里都会被重置为空，解决方法是在你博客项目下的public文件夹中创建一个名为CNAME的文件，用文本编辑器打开并填入你的域名，这样就不用每部署一次就来填写一次自己的域名了。

此时访问你的域名，就会直接跳转到你的github page项目中。

##  7. <a name='cloudflarecdn'></a>使用cloudflare做cdn加速。

>这里我不去讲复杂的概念，大家只要清楚，github在国内访问速度过慢，而cloudflare可以免费提供每天十万次的点击加速，对我们的博客来说完全足够，了解这点就好。

###  7.1. <a name='cloudflare-1'></a>打开cloudflare注册并登录

注册登录这一步不再细说。

###  7.2. <a name='cloudflare-1'></a>将自己的域名交给cloudflare管理

点击左侧的管理域（或者账户主页）

![alt text](image-18.png)

点击添加域

![alt text](image-19.png)

输入自己的域名：

![alt text](image-20.png)

选择免费计划。

###  7.3. <a name='DNScloudflare'></a>将自己域名的DNS服务器改为cloudflare

将自己的域名添加到cloudflare后，点击配置自己域名的DNS配置。拉到最下方，可以看到cloudflare的DNS服务器域名，接着打开自己购买域名的网站，把DNS服务器改成这两个。

>注：一切跟DNS相关的东西可能都需要等待时间，等待当地及其他地区的DNS缓存刷新，这个过程可以不用着急，通过域名有时不能访问是正常的。


![alt text](image-21.png)

###  7.4. <a name='cloudflareDNSgithubip'></a>通过cloudflare添加DNS记录，使域名指向github ip，以便加速生成。

添加记录，值为github的ip地址：

![alt text](image-22.png)

添加记录选择A记录，填入自己的域名（写入@即可）和github ip，使域名指向github，并且通过cloudflare代理。

![alt text](image-23.png)

>注：四个ip地址都要添加。

保存，然后等待。前面提到过，一切跟DNS有关的东西都需要等待，所以静静等待就好。如何测试加速生成了，建议挂着梯子，或者代理加速器乱七八糟的东西，如果必须要加速才能访问就说明还没生效，如果不加速就能访问成功，说明已经生效。