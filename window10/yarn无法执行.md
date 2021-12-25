# PowerShell yarn : 无法加载文件 C:\Users\Admin\AppData\Roaming\npm\yarn.ps1,因为在此系统因为在此系统上禁止运行脚本。

2020-05-11阅读 1.3K0

![img](https://ask.qcloudimg.com/http-save/yehe-2353021/rvsrip2ia6.jpeg?imageView2/2/w/1620)

新版win10 安装的时候会出现：

```javascript
PowerShell yarn : 无法加载文件 C:\Users\Admin\AppData\Roaming\npm\yarn.ps1,因为在此系统因为在此系统上禁止运行脚本。
```

这个时候需要

解决方法

1：搜索powershell，以管理员方式运行powershell 2：使用命令更改计算机的执行策略

```javascript
PS C:\Users\Administrator> set-ExecutionPolicy RemoteSigned

执行策略更改
执行策略可帮助你防止执行不信任的脚本。更改执行策略可能会产生安全风险，如 https:/go.microsoft.com/fwlink/?LinkID=135170
中的 about_Execution_Policies 帮助主题所述。是否要更改执行策略?
[Y] 是(Y)  [A] 全是(A)  [N] 否(N)  [L] 全否(L)  [S] 暂停(S)  [?] 帮助 (默认值为“N”): y
```

这样设置即可修复该bug

3:查看执行策略

```javascript
get-ExecutionPolicy
```

