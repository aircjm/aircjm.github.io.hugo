---
cards-deck: Default
createAt: 2021-09-29 10:09:01
draft: false
publish: true
title: "window\u4E0B\u7684\u8F6F\u4EF6\u5B89\u88C5\u7BA1\u7406\u5DE5\u5177scoop"
updateAt: 2021-09-29 16:31:04
---

tags: #windows/scoop #工具

# 安装
## 设置环境
```powershell
#home路径
$env:SCOOP='D:\Applications\Scoop'
[Environment]::SetEnvironmentVariable('SCOOP', $env:SCOOP, 'User')

$env:SCOOP_GLOBAL='D:\Applications\GlobalScoopApps'
[Environment]::SetEnvironmentVariable('SCOOP_GLOBAL', $env:SCOOP_GLOBAL, 'Machine')
```

## 安装
在 PowerShell 中输入下面内容，保证允许本地脚本的执行：
```cmd
set-executionpolicy remotesigned -scope currentuser
```

然后执行下面的命令安装 Scoop：
```cmd
Invoke-Expression (New-Object System.Net.WebClient).DownloadString('https://get.scoop.sh')
```

脚本执行完就好了



```
.\install.ps1 -ScoopDir 'D:\Applications\Scoop' -ScoopGlobalDir 'D:\Applications\GlobalScoopApps' -NoProxy
```

## 常用命令
```bash
#重置应用以解决冲突,会重置环境变量,快捷方式等..
scoop reset *

# 更新 scoop 及软件包列表
scoop update

## 安装软件 ##
# 非全局安装（并禁止安装包缓存）
scoop install -k <app>
# 全局安装（并禁止安装包缓存）
sudo scoop install -gk <app>

## 卸载软件 ##
# 卸载非全局软件（并删除配置文件）
scoop uninstall -p <app>
# 卸载全局软件（并删除配置文件）
sudo scoop uninstall -gp <app>

## 更新软件 ##
# 更新所有非全局软件（并禁止安装包缓存）
scoop update -k *
# 更新所有软件（并禁止安装包缓存）
sudo scoop update -gk *

## 垃圾清理 ##
# 删除所有旧版本非全局软件（并删除软件包缓存）
scoop cleanup -k *
# 删除所有旧版本软件（并删除软件包缓存）
sudo scoop cleanup -gk *
# 清除软件包缓存
scoop cache rm *
```



### 代理设置
Scoop 默认使用的是系统代理，如果你想手动指定代理，可以输入下面的命令。需要注意的是只支持 http 协议。

```bash
scoop config proxy localhost:1080
```

设置完可以通过`scoop config proxy`查看。
如果你想取消代理，那么输入下面的命令，这将会恢复使用系统代理。
```bash
scoop config rm proxy
```

###  aria2下载


#github

https://github.com/lukesampson/scoop