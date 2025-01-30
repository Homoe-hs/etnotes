---
对象类型: 
aliases: 
tags: 
number headings: auto, first-level 1, max 5, contents ^toc, 1.1.
---
# 1. 现状

工业 4.0（industry 4.0）和数字转型（digital transformation）带来了更多数字资产，使得更容易受到网络攻击

# 2. 防护

## 2.1. 技术手段

[[密码学]]（Cryptography）、[[防火墙]]（Firewalls）、软件更新、侵入检测（invasion detection）、使用强密码（use strong passwords）、[[2FA|双重身份验证]]（two factor authentification， 2FA）、定期备份。

## 2.2. 非技术手段

为员工提供定期安全培训以帮助他们识别潜在威胁, 并在点击链接或从未知来源下载附件时保持谨慎。

# 3. 未来应对

总是存在网络安全攻击，并且随着工业 4.0 和数字化转型的发展，被攻击的概率也会随之增长。能做的就是通过实施更多的保护来

# 4. 网络安全的目标

> [! tip] Linux 的权限类型
> 这里其实可以和 linux 的权限系统对应起来。linux 的权限类型分为读（r）、写（w）、执行（x）三类。机密性相当于禁止读，完整性相当于禁止写，可用性则是赋予读写权限。

网络安全的目标是实现 CIA ：
- Confidentiality：机密性，意味着防止未经授权的数据访问/共享；
- Integrity：完整性，意味着未经授权的人不得更改数据；
- Availability：可用性，意味着信息对于授权方应保持一致且易于访问。

> [!note] 一些术语
> - [[验证]]（Authentication）：保证沟通实体即为其声称的实体（非伪装）
> - [[抗抵赖]]（Non-repudiation）：防止一个实体否认其已经创建的消息（对内容负责）
