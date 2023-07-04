---
layout: default
title: 工具
---

> [首页](/index.html)

## Github 网站访问加速

### 第1步，打开 *https://www.ipaddress.com/* 查询出域名当前对应的最有IP

> 或者打开网站 *http://tool.chinaz.com/dns/* 在A类型中填写 github.com 进行监测

分别查询出下面3个网址对应的IP地址：

> github.com  
> &emsp; 140.82.113.3, 140.82.113.4  
> assets-cdn.github.com  
> &emsp; 185.199.108.153, 185.199.109.153, 185.199.110.153, 185.199.111.15  
> github.global.ssl.fastly.net  
> &emsp; 199.232.69.194

### 第2步，修改本地电脑系统 \etc\hosts 文件

Windows 文件路径：C:\WINDOWS\system32\drivers\etc  
Linux 文件路径：/etc/hosts  
直接在末尾追加以下代码：

``` 
140.82.113.3 github.com  
140.82.113.4 github.com  
185.199.108.153 assets-cdn.github.com  
185.199.109.153 assets-cdn.github.com  
185.199.110.153 assets-cdn.github.com  
185.199.111.153 assets-cdn.github.com  
199.232.69.194 github.global.ssl.fastly.net
```

> 关于 \etc\hosts 修改后无法保存的解决方案   
> &emsp; 方法一、关闭杀毒软件，再修改  
> &emsp; 方法二、右击hosts文件，选择属性>安全>编辑，将user用户设置为完全控制  
> &emsp; 方法三、以管理员身份运行

### 第3步，刷新dns缓存

修改后会直接生效，无需刷新DNS缓存，因为hosts优先级大于DNS域名解析。  
如未生效，重启操作系统或使用命令刷新：

Windows命令：ipconfig /flushdns  
Linux命令：systemctl restart nscd
