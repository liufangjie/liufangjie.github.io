---
layout: post
title: windows使用经验
---
{{ page.title }}
================

# 设置大小写敏感(case sensitive)

修改注册表: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel\obcaseinsensitive

0表示大小写敏感
1表示大小写不敏感

参考资料:
[a-file-system-that-was-case-sensitive-becomes-case-insensitive-after-y](https://support.microsoft.com/en-us/help/929110/a-file-system-that-was-case-sensitive-becomes-case-insensitive-after-y)
[how-do-you-make-windows-7-fully-case-sensitive-with-respect-to-the-filesystem](https://superuser.com/questions/266110/how-do-you-make-windows-7-fully-case-sensitive-with-respect-to-the-filesystem)

上述设置目前没有生效。

# 查看端口占用

netstat -ano | findstr {查询端口号}