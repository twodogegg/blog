---
title: "Nginx 使用阿里云的 SSL证书服务 配置HTTPS"
date: 2020-03-22T09:08:53+08:00
dropCap: false
slug: "nginx-use-aliyun-ssl-config-https"
description: "试了好几种方法还是觉得用阿里云的ssl证书加上自己配置笔记适合自己"
---

## 前言

需要给自己的网站配置和 https。看了网上一些教程。好多都是用 linux 直接生成证书[^1]。然后配置的时候才发现要选个域名证书，配置的时候没有这么说啊。然后就算了。想到了阿里云，阿里云感觉和开发相关的服务啥都有。我就直接搜索 `https`。果然让我搜到了[^2]

## 购买 ssl 免费证书

![购买免费的ssl](/images/WX20200322-091700@2x.png)

## 申请证书

购买完成以后到证书控制台。有个证书申请，填写实际情况即可。 域名验证方式由于我的域名是阿里云购买的所以直接选择自动 DNS 验证，根据情况而定。CSR 生成方式默认

## 添加一个域名解析

申请证书上面的步骤完成以后，根据提示新增一个域名解析。然后等待审核即可

## Nginx 安装证书[^3]

下载证书以后再服务器类似如此配置

个人配置参考

```
server {
    listen 80; #同时访问 80 和 433 端口
    listen 443 ssl;
    ssl_certificate cert/xxxx.pem;   #将domain name.pem替换成您证书的文件名。
    ssl_certificate_key cert/xxxx.key;   #将domain name.key替换成您证书的密钥文件名。
    ssl_ciphers ECDHE-RSA-AES128-GCM-SHA256:ECDHE:ECDH:AES:HIGH:!NULL:!aNULL:!MD5:!ADH:!RC4;
    ssl_protocols TLSv1 TLSv1.1 TLSv1.2;   #使用该协议进行配置。
    server_name  localhost; #将localhost修改为您证书绑定的域名，例如：www.example.com。
    ssl_prefer_server_ciphers on;
    ssl_session_timeout 5m;

    .
    .
    .
}
```

## 其他

记得服务器要开放 443 端口，如果是 docker 环境 nginx 端口 需要抛出 443 端口 "443:443"

---

[^1]: [有点懵逼，配置的证书看起来不用区分域名。然后证书好多啊](https://blog.csdn.net/liuzk2014/article/details/89538212?depth_1-utm_source=distribute.pc_relevant.none-task&utm_source=distribute.pc_relevant.none-task)
[^2]: [阿里云 ssl 证书服务](https://www.aliyun.com/product/cas?spm=5176.10695662.958455.1.21d262a6uFb4R9)
[^3]: [安装证书这部分挺详细的](https://help.aliyun.com/document_detail/98728.html?spm=5176.2020520163.0.0.493a56a7nJgiiv)
