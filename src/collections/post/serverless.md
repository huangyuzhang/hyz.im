---
title: Serverless资源收集
slug: serverless
date: 2024-01-26
authors:
  - simon
tags:
  - 工具
isFeatured: false
toc: true
description: Serverless资源对于个人项目、小型企业的开发者来说是极好的。首先大多有一些免费的额度可以使用。其次支持的服务很多，基本都可以快速和git打通完成部署。再来可以省下很多的运维投入。因此可以说是一种面向未来的服务。
---
Serverless是一种可以让独立开发者延年益寿的服务范畴，他们大部分拥有不错的免费额度，这样一来我们就可以达到几乎零成本实现自己的应用的目的。现在还有一些云容器厂商也支持一定的免费额度，这边来大致介绍一下吧！



## OSS



- Backblaze：提供免费额度的OSS服务（10G存储免费，每天1G下载免费，如果用CloudFlare中转则下载完全免费）
- Cloudflare R2：包含在Workers内的S3兼容的对象存储，没有出口费用，额度：储存10GB，A类操作 100万次/月，B类操作1000万次/月，出口带宽免费。



## Pass/云部署/云容器


- Vercel：云部署服务商
- Netlify：云部署服务商
- Cloudflare Worker：云部署服务商
- Firebase Hosting：谷歌提供的网站托管服务
- Deno Deploy：Deno旗下的一个云部署平台，
- Railway：云应用部署平台，Github 认证并且绑定信用卡后每月提供 $5 的免费额度 Hobby Plan。支持 Python、Node.js 等。Hobby Plan 不支持选择区域。
- 4Everland：面向 web3 的云部署服务商，提供免费额度的 IPFS 和 Arweave 存储等
- Fly.io：需绑定信用卡，提供一定免费额度的云服务

  - 免费额度可参考：https://fly.io/docs/about/pricing/#free-allowances
  - 有较大免费额度3Gb?的postgres集群：https://fly.io/docs/postgres/
- Render：云应用托管，可以快速部署多种应用，静态网站、定时任务等，适合做API。

  - 免费额度可参考：https://render.com/docs/free（免费pg数据库只有90天有效期）
  - 支持选择区域：美国、德国、新加坡
  - 免费版本应用15分钟不活跃暂时挂起，有访问再自动启动


## 云数据库


- Cloudflare D1：包含在Cloudflare Worker中的SQL数据库，可以通过Workers和Pages访问，免费额度（5GB存储，读5百万行/日，写10万行/日）
- Cloudflare Worker KV：worker中提供的KV数据库，免费额度（1GB存储，日10万读，1000写，1000删、1000List），只能在worker中使用
- Supabase：推荐！提供免费500MB的Postgres数据库。核心定位是BaaS，因此支持以app的形式建立服务，提供丰富的API，还提供诸如Auth、Storage、Edge Function等搭建应用所需的完整功能，且都有免费额度，不活跃被暂停后可以restore。
- PlanetScale：推荐！提供免费5GB的MySQL数据库，需要绑定信用卡
- Upstash：免费250MB的Redis和Kafka存储，可以通过多个组织创建多个数据库，⚠️不活跃会直接删除
- Neon：提供免费3GB的Postgres数据库（闲置自动挂起，连接后自动恢复）
- CockroachLabs：免费额度的PGSQL数据库（50 million RUs and 10 GiB storage）
- MongoDB Atlas：免费500Mb的MongoDB数据库
