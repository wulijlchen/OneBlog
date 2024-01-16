----

# 重要声明

项目源码地址 [Github](https://github.com/zhangyd-c/OneBlog)

----


# 功能简介

- **Docker一键部署**：支持 Docker 的方式一键启动服务
- **广告位管理**：支持五种广告位：首页开屏广告、侧边栏顶部、侧边栏底部、文章详情底部、评论框顶部，站长可以随时随意更换自己的广告链接，赚外快不成问题！
- **多种编辑器**：支持 wangEditor、Markdown 和 TinyMCE 等多种文章编辑器，可以自行选择
- **自动申请友情链接**：在线申请友情链接，无需站长手动配置，只需申请方添加完站长的连接后自行申请即可
- **百度推送**：支持百度推送功能，加速百度搜索引擎收录博文
- **评论系统**：自研的评论系统，支持显示用户地址、浏览器和 os 信息，后台可审核评论、开启匿名评论、回复和邮件通知评论
- **权限管理**：后台配备完善的 RBAC 权限管理，前台文章支持密码访问、登录访问等多种权限验证策略
- **完善的 SEO 方案**：自带robots、sitemap 等 seo 模板，实现自动生成 robots 和 sitemap
- **实时通讯**：管理员可向在线的用户实时发送消息
- **系统配置支持快速配置**：可通过后台手动修改诸如域名信息、SEO 优化、赞赏码、七牛云以及更新维护通知等
- **多种文件存储**：集成七牛云、阿里云OSS，实现文件云存储，同时支持本地文件存储
- **文章搬运工**：集成[blog-hunter](https://gitee.com/yadong.zhang/blog-hunter) 实现“文章搬运工”功能，支持一键同步imooc、csdn、iteye或者cnblogs上的文章，可抓取列表和单个文章
- **第三方授权登录**：集成 [JustAuthPlus（JAP）](https://gitee.com/fujieid/jap) 实现第三方授权登录
- **自定义网站内容**：管理员可自定义“关于本站”、“留言板”、“友情链接”、“免责声明”、“Footer”、“鼠标点击时的气泡文字”、“热门搜索的待选项”等内容
- **自定义页面**：管理员可添加自定义的页面
- **流控**：针对异常IP的连续大量访问，系统会自动封禁该IP。

----

# 模块划分

| 模块  | 释义 | 备注 |
| :------------: | :------------: | :------------: |
| blog-core | 核心业务类模块，提供基本的数据操作、工具处理等 | 该模块只是作为核心依赖包存在 |
| blog-codegen | 代码生成器 |
| blog-admin | 后台管理模块 | 该模块作为单独项目打包部署 |
| blog-web | 前台模块 | 该模块作为单独项目打包部署 |
| blog-file | 文件存储功能模块 | 支持local、七牛云和阿里云OSS |


# 技术栈

- docker
- docker-compose
- Springboot 2.3.4.RELEASE
- Apache Shiro 1.7.1
- Logback
- Redis
- Lombok
- Websocket
- MySQL、Mybatis、Mapper、Pagehelper
- Freemarker
- Bootstrap 3.3.0
- wangEditor
- Markdown
- jQuery 1.11.1、jQuery Lazyload 1.9.7、fancybox、iCheck
- 阿里云OSS
- 七牛云
- Nginx
- kaptcha
- webMagic
- ...


# 快速开始

## Docker Compose（推荐）

Compose 是用于定义和运行多容器 Docker 应用程序的工具。通过 Compose，您可以使用 YML 文件来配置应用程序需要的所有服务。然后，使用一个命令，就可以从 YML 文件配置中创建并启动所有服务。
使用之前需要先安装docker环境，建议版本为17.06.0-ce以上版本
1. 下载源码，安装maven环境，
打包项目 `mvn clean package -Dmaven.test.skip=true -Pdev`，放到服务器
2. 进入 `docs/docker` 目录
3. 按照注释修改 `.env` 文件
4. 执行 `docker-compose -p oneblog up -d`

## 源码方式

> `blog-web` 和 `blog-admin` 的运行方式一样

1. 使用IDE导入本项目
2. 新建数据库`CREATE DATABASE dblog;`
3. 导入数据库`docs/docker/mysql/dblog.sql`
4. 初始化数据库`docs/docker/mysql/init_data.sql`
5. 修改配置文件，mysql、redis、mail配置在`[blog-core]/resources/config/application-center.yml`配置文件中
6. 运行项目：直接运行 `blog-web/src/main/java/com/zyd/blog/BlogWebApplication.java` 或者 `blog-admin/src/main/java/com/zyd/blog/BlogAdminApplication.java`
7. 浏览器访问`http://127.0.0.1:{port}`

> 后台默认账号密码：root/123456

# 开源协议

[![license](https://img.shields.io/badge/license-GPL%20v3-yellow.svg)](https://gitee.com/yadong.zhang/DBlog/blob/master/LICENSE)
