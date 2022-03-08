---
layout: post
title: windows
---
{{ page.title }}
================

# デバイス管理、デバイスを再度有効化する方法

OS:win 10

```html
[設定] - [アカウント] - [職場または学校にアクセスする] から接続済みになっている（実際には管理者が削除している）アカウントをクリックして [切断] を実行します。

その後に、もう一度同じ画面から登録を行ってください。
```

[デバイス管理、デバイスを再度有効化する方法](https://answers.microsoft.com/ja-jp/msoffice/forum/all/%E3%83%87%E3%83%90%E3%82%A4%E3%82%B9%E7%AE%A1/ef8e7540-d857-4c27-9a4c-1ea6d135048e)

# 查看系统默认编码格式

在cmd窗口输入`[System.Text.Encoding]::Default`

# 快速拷贝文件

可以使用[robocopy](https://docs.microsoft.com/en-us/windows-server/administration/windows-commands/robocopy)工具，该工具在windows server 2008及win7以后的版本默认提供

[robocopy 版本](https://en.wikipedia.org/wiki/Robocopy)

# 共享文件夹取消共享后锁图标不消失

设置共享添加Everyone用户后图标消失，然后通过高级共享取消共享即可

# 设置大小写敏感(case sensitive)

修改注册表: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager\kernel\obcaseinsensitive

0表示大小写敏感
1表示大小写不敏感

参考资料:
[a-file-system-that-was-case-sensitive-becomes-case-insensitive-after-y](https://support.microsoft.com/en-us/help/929110/a-file-system-that-was-case-sensitive-becomes-case-insensitive-after-y)
[how-do-you-make-windows-7-fully-case-sensitive-with-respect-to-the-filesystem](https://superuser.com/questions/266110/how-do-you-make-windows-7-fully-case-sensitive-with-respect-to-the-filesystem)

上述设置目前没有生效。

# 查看端口占用

```
netstat -ano | findstr {查询端口号}
```

上述命令输出的最后一列为pid

```
taskkill /f /pid pid
例如：taskkill /f /pid 12345
```

参考：[https://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows](https://stackoverflow.com/questions/48198/how-can-you-find-out-which-process-is-listening-on-a-port-on-windows)

