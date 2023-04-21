---
title: 一次基于 Jamstack 的博客尝试
slug: 一次基于Jamstack的博客尝试
date: 2023-04-22
image: 
authors:
  - simon
tags:
  - 爱好
description: 关于这个博客系统的设计哲学以及技术栈详解，终于把坑填上了！
isFeatured: false
toc: true
eleventyExcludeFromCollections: true
---

## 导读

终于来填坑了！我在[《谈谈如何建立数字影响力》](/post/谈谈如何建立数字影响力/)的最后提到了这个博客是基于一种比较现代化的概念建立的，这个概念就是 Jamstack。JAM 分别指 **J**avaScript、**A**PI 以及 **M**arkup。它将静态网站生成器、前端框架和CDN等技术结合起来，以提供更快、更安全、更可靠的Web体验。具体的介绍可以参考[Jamstack.org](https://jamstack.org/)。

## 什么是Jamstack

在我的理解中，与其说 Jamstack 是一种技术栈，不如说它代表了新一现代 web 的设计和构建理念：核心是将 Web 体验层、数据、业务逻辑分离（也可以理解为独立成模块），这样就提高了各部分的灵活性、可扩展性，也更便于维护和调整。但是 Jamstack 并不适用于所有 web 场景，可能较为适合的场景比如：

* 静态网站：Jamstack最初是为静态网站生成器而设计的，它可以帮助开发者快速构建高性能的静态网站。
* 前端应用：Jamstack可以结合现代的前端框架（如React、Vue等）来构建动态的Web应用，同时还可以利用CDN等技术来提高性能和可靠性。
* API服务：Jamstack可以利用现代的API服务（如GraphQL、RESTful API等）来获取数据，并将数据缓存到CDN中，以提高性能和可靠性。

因此，作为个人的独立博客而言，Jamstack 可能是一个非常好的设计理念。

## 我对博客的理解

正如我在[《重拾旧好》](/post/重拾旧好/)中提到的，如果你真的要写一些文字内容，目前有许多的平台都可以满足你的需求，而且你还更容易收货一些追随者。但是在我看来，一旦你选择了某个平台，你就不可避免地要接受向平台妥协的现实。这种妥协是多方面的，比如你的写作风格需要更加迎合平台的流量算法；你能发布的内容形式受限于平台的限制；你的内容和媒体变相授权给了平台使用。

> 插播：
> 前段时间我了解到了 DIYgod 大佬写的链上博客平台 [xlog.app](https://xlog.app/)。这让我感到眼前一亮，是我一直想做但是没能力做的事情。至少在内容所有权上，你创作的内容被写在了他们构建的EVM兼容区块链 Crossbell上。但是上链也需要接受不少妥协，比如你所有的更改都是可查的，一些更改后不想再展示的内容，如果碰到 fishy 的人那还是能给你挖出来的。因此，你需要自己做一些研究（do your own research），对于纯分享来说这可能会是一个很好的平台。

没错，人生本就充满了妥协。但当我把这个博客当作我和自己、和世界在更深层面沟通的时候，我想要更加自由一些。

两年前我开始了自己搭建 Fizzy-Jam 的过程。当然这里说的自己搭建，并不是指我不用任何现有技术，相反地，我尽可能使用成熟的开源技术。取名叫 Fizzy-Jam，则是因为这是我从之前给自己的 Ghost 博客写的主题 Fizzy 移植过来的，Jam 则是它遵循了 Jamstack 的理念。

我希望它是一个**低成本、低耦合、高可用、低维护、可以长期存在**的博客系统。我把设计的理念写在了github介绍的最前面：

> ## 🤔 Philosophy [^fizzy-jam:github]
>
> 1. Everything lives in a git repo. This means you can host the site on GitHub, rather than paying monthly fees for web servers and database.
> 2. An user-friendly yet pre-configured CMS. This allows you to focus on creating wonderful content, not the architecture or code. (you may also use the CMS offline, then push the static site to Github manually to activate CI)
> 3. Decoupled everywhere. Customize the site is fun by adding micro-services.

[^fizzy-jam:github]:[Fizzy-Jam Github 仓库](https://github.com/huangyuzhang/Fizzy-Jam)

相比如传统意义上的搭建网站，

1. 所有的非媒体数据都存储在 git 仓库中（比如你的 github 仓库），所有媒体数据都通过 OSS 进行存储（免费的额度十分够用）；
2. 一个已经定制了的基于 git 的 CMS 系统，因此你不再需要服务器便可以在浏览器中对博客内容进行管理（同时，本地的撰写操作是独立的）；
3. 任何模块都是独立存在的，因此你可以按自己的需求去掉/加入新的模块。
   1. 比如除了文章、页面这样的基本collection之外，你也可以新增商品这样的集合并创建对应的页面；
   2. 如果你不喜欢默认的评论系统，你可以选择关闭或者自己更换；
   3. 如果你需要增加i18n的支持，也可以自己添加。

这边不对具体使用的技术进行更多的介绍了，感兴趣的朋友可以自己去看 Github 仓库 [^fizzy-jam:github]。

## 来一起搭建吧🎉

如果你对博客有类似我这样的需求，那么不妨一起来尝试一下搭建一个完全属于你自己的博客。这个过程不难，但是对于没有基础的朋友来说有一定的学习成本，所以我会试着尽可能详细说明。

### 预期的准备工作

你需要做的大概有这些，除此之外都已经帮你准备好了：

1. 学习 Markdown 语法
2. 一个域名（只有这个需要花钱）
3. 一个 Github 账号，复制博客程序后用做远端仓库，存储博客内容；
4. 一个 有一定免费额度的 OSS 服务商，用来存放我们的图片和其他媒体文件，如果没有的话可以看下面推荐的（非必须）；
5. 一个 Netlify 或者 Vercel 账号用来自动构建并托管我们的网站（非必须）。

> 暂不考虑将网站部署在国内平台，因为涉及备案等额外门槛，有需要的朋友可以在以后自行研究。

从这里你可以大概知道为什么这是一个可以做到“低成本、低耦合、高可用、低维护、可以长期存在”的博客系统。因为在将系统部署到云端的时候，我们在每个环节都用了独立的解决方案。比如用了github仓库，其实也可以使用其他的 git 平台；而 OSS 服务商只是为了帮助我们存储媒体文件，你可以随时更换服务商；类似Netlify和Vercel这样的静态网站托管服务提供商也还有一些，比如 CloudFlare。

当然，如果你的博客也是以文字内容为主，那么第3、4步实际上是可以跳过的，因为github仓库本身也有一定的内容存储空间，另外 Github Pages 也可以直接帮我们完成页面的构建和托管，甚至github也提供了免费的二级域名。我们使用自己的域名、OSS和静态网站托管服务，主要是为了提升网站的可用性和访问速度（尤其是在国内）。

当我们把网站部署的各个环节分散到专门的提供商时，我们就可以最大程度利用每个提供商的优点。因此当我们第一次配置完成之后，后续的维护成本是很低的。我们就可以专注于创作内容了。

### 工作方式

先简单讲一下整体的底层发布流程逻辑，即使你选择使用web的创作方式，底层也是在执行这些操作，这样可以方便你更好地了解后面每一步我们在干什么。

1. 先将 Fizzy-Jam  [^fizzy-jam:github]项目拷贝到本地，并配置上游以保证可以持续更新
2. 在 Github 中创建一个仓库，存储你的 Fizzy-Jam 项目
3. 创作内容 😌，期间图片等多媒体文件可以存储到 OSS 中
4. 将创作完的内容打包为一次更改提交同步到 Github 仓库
5. 利用 Netlify 从 Github 中同步仓库，并自动触发网站的自动构建

