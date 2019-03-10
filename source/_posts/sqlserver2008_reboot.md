---
title : SQLServer2008安装一直显示重启计算机
categories : Sqlserver2008
---
>
进入注册表编辑器，依次打开HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Session Manager，找到“PendingFileRenameOperations”值
删掉，即可