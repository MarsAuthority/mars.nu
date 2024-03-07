---
title: 互联网菩萨系列之免费个人域名邮箱：Cloudflare + Gmail + Resend 快速搭建个人域名邮箱
draft: false
tags:
  - 互联网菩萨
  - 独立开发
---
 
![](attachment/cef73b83e6fb45bfb89c17bc3dd5389c.png)
> 作为独立开发者，少不了使用个性域名作为邮箱，这里和大家分享一下我的个人免费域名邮箱方案：「Cloudflare + Gmail + Resend」。

作为独立开发者，少不了使用个性域名作为邮箱，这里和大家分享一下我的个人域名邮箱方案：「**Cloudflare + Gmail + Resend**」。
本方案通过白嫖互联网免费服务来实现，**存在一定的使用额度限制**，只适用于小规模或个人使用，具体如下：
- 接收邮件：使用Cloludflare 的服务，免费用户不支持大于 25 MiB 的邮件；邮件规则数为20个。
- 发送邮件：使用 Resend 的服务，免费用户支持 1 个自定义域名，发送额度每天 100，每月 3000。
# 1. 整体流程
![](attachment/92b26598610355c4d159d6997ee03c16.png)

# 2. 准备工作
拥有一个域名，且域名的 dns 在 Cloudflare 管理，参考[Get started on Cloudflare · Cloudflare Docs](https://developers.cloudflare.com/learning-paths/get-started/)。
# 3. 接收邮件：Cloudflare配置
## 3.1. 配合邮件转发：Email->Email Routing
根据提示，添加自定义地址、转发的邮箱地址和相关DNS配置。
![](attachment/2948d6586f2410260f1a393cbdc63f1d.png)
![](attachment/5b8a5f379d72495cbbdde9b4ae759e26.png)
![](attachment/cf52a7dc9f41926612921f53757c32ab.png)

🎉 大功告成，到这里**接收邮件**就搞定了；可以发送邮件到你刚刚配置的地址上试试。
# 4. 发送邮件：Resend配置
## 4.1. 注册并绑定域名

注册[Resend](https://resend.com/)后，绑定你的域名，并去Cloudflare做对应的DNS配置修改，验证生效即可。
![](attachment/b9cd9e6bfb1a731126432678f67a406f.png)

## 4.2. 创建API KEY并获取SMTP信息
在API Keys 标签下申请新的API Key；这里的Key后续会作为SMTP的密码来使用。
![](attachment/c09580969a1ff7380f34035afa503f0f.png)

去Settings 查看 smtp 设置，用于后续在Gmail的配置。
![](attachment/1b1d69cf3765874b7dfa0274fc0ab59a.png)

## 4.3. 在Gmail添加对应的自定义地址的邮箱
找到 Settings -> Accounts and Import -> 在 Send mail as 中点击 Add another email address。
![](attachment/38f4050d18f2f9b4a60d4fdaa7d50e4a.png)

填入名字和用于发送邮件的账号，及刚刚拿到的Resend smtp配置信息。
![](attachment/d4050ad2a9fc3209a6ef8c3a6afe8929.png)
![](attachment/2a73389f1d28226661c0d4ec7c18e8e8.png)

之后会收到来自 Gmail 的确认邮件，点击 confirm 即可完成配置。
![](attachment/d2929f5297da953b9706e30426c849c3.png)

🎉 大功告成，到这里**发送邮件**就搞定了；在Gmail 的发送邮件页面，选择你刚刚配置邮件，就可以使用该邮箱发送邮件了。
![](attachment/bb2f3aa7b4125e31c891c095073b181d.png)