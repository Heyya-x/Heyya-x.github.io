---
title: overleaf/toolkit
date: 2022-11-09 20:12:16
tags: [overleaf, docker]
---

# 服务器部署overleaf/toolkit服务

> 记录一下折腾了好久本地服务，每次部署后都无法使用XeLaTeX编译，由于找不到合适解决办法，采用笨方法，导致每次都是删除镜像重新来过，而安装完整版的TexLive又十分的漫长，可以说是踩了个大坑，QAQ。

## Docker 安装

参考<a href="https://docs.docker.com/engine/install/" target="_blank">官方链接</a>，不再赘述。

## 克隆仓库

``` git
#克隆到用户根目录的ovealeaf文件夹下 
git clone https://github.com/overleaf/toolkit.git ~/overleaf
```

## 修改配置文件

> 若需使用到XeLaTeX，需要在up之前修改配置文件。

``` bash
cd lib
vim docker-compose.base.yml
```

修改后配置文件内容如下：

``` yaml
---
version: '2.2'
services:

    sharelatex:
        restart: always
        image: "${IMAGE}"
        container_name: sharelatex
        volumes:
            - "${SHARELATEX_DATA_PATH}:/var/lib/sharelatex"
        ports:
            - "${SHARELATEX_LISTEN_IP:-127.0.0.1}:${SHARELATEX_PORT:-8443}:80"
        environment:
          SHARELATEX_MONGO_URL: "${MONGO_URL}"
          SHARELATEX_REDIS_HOST: "${REDIS_HOST}"
          REDIS_HOST: "${REDIS_HOST}"
          PATH: /usr/local/texlive/2022/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
        env_file: ../config/variables.env
```

1. 修改PATH内容为 `PATH: /usr/local/texlive/2022/bin/x86_64-linux:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin`
2. 同时可将ports的80端口修改为8443（此步可跳过，若不修改则为80）。

> 需注意的是，在up后，修改部分配置要再次up才能生效，这意味着若你安装了完整的LaTeX，up后需要再次安装。所以请在up前配置好文件。

## 启动镜像

```bash
bin/up
```

进入镜像，安装完整版TexLive

```bash
docker exec -it sharelatex /bin/bash
# 更换镜像源，这里使用清华的源，若地址改变，可访问：https://mirrors.tuna.tsinghua.edu.cn/help/CTAN/
tlmgr option repository https://mirrors.tuna.tsinghua.edu.cn/CTAN/systems/texlive/tlnet
tlmgr update --self
tlmgr install scheme-full
```

若 `tlmgr update --self` 更新失败，可用`/usr/local/texlive/2022/bin/x86_64-linux/tlmgr update --all` 其中的`2022` 需更换为tlgmr相应的目录，可 `cd /usr/local/texlive/` 进入文件夹查看。

安装完整版需要下载4千多个包，需等待许久。漫长等待QAQ

## 补全中文字体

安装完成后，重启镜像

```bash
exit
bin/restart
```


> `Windows`用户系统字体文件路径：`C:\Windows\Fonts`
> `macOS`用户系统字体文件路径：`/System/Library/Fonts`

以`macOS`为例，把本地所有字体导入到服务器内

```bash
docker cp /System/Library/Fonts sharelatex:/usr/share/fonts/
```

刷新服务器缓存

```bash
# 进入容器内
docker exec -it sharelatex bash
cd /usr/share/fonts/ch_fonts
# 刷新缓存命令
fc-cache
# 查看字体缓存是否刷新
fc-list | grep ch_fonts
```

## 创建账号

访问本地服务`localhost/launchpad:8443` ，前面已经修改端口号为`8443`，若未修改则无需加上端口号。

进入页面输入账号、密码，创建管理员账号。



PS：使用XeLaTeX的方法参考自<a href="https://github.com/overleaf/overleaf/issues/1055" target="_blank">Issues#1055</a>，刚踩完一个坑，发博客的时候发现博客炸了！！！

至此，本地服务器上的overleaf已经搭建完成，且可以使用XeLaTeX编译中文的字体的.tex文件。
