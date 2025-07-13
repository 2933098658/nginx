以下是NGINX官方README文档的专业中文翻译：

------

​      

NGINX（发音为 "engine x" 或 "en-jin-eks"）是全球最流行的Web服务器，也是高性能负载均衡器、反向代理、API网关和内容缓存解决方案。

NGINX是免费开源软件，基于简化的[类似BSD的2条款许可证](https://tencent.yuanbao/LICENSE)发布。

企业级发行版、商业支持及培训服务由[F5公司](https://www.f5.com/products/nginx)提供。

> [!重要提示]
>  本文档目标是为NGINX新手用户提供基础结构化介绍，详细安装、构建、配置和调试指南请参阅[完整NGINX文档](https://nginx.org/en/docs/)。这些文档还包含更详细的[初学者指南](https://nginx.org/en/docs/beginners_guide.html)、操作指南、[开发指南](https://nginx.org/en/docs/dev/development_guide.html)以及完整的模块和[指令参考](https://nginx.org/en/docs/dirindex.html)。

# 目录

- 工作原理
  - [模块](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#模块)
  - [配置](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#配置)
  - [运行时](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#运行时)
- 下载与安装
  - [稳定版与主线版二进制包](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#稳定版与主线版二进制包)
  - [Linux二进制安装流程](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#linux二进制安装流程)
  - [FreeBSD安装流程](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#freebsd安装流程)
  - [Windows可执行文件](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#windows可执行文件)
  - [动态模块](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#动态模块)
- NGINX快速入门
  - [安装SSL证书与启用TLS加密](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#安装ssl证书与启用tls加密)
  - [负载均衡](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#负载均衡)
  - [速率限制](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#速率限制)
  - [内容缓存](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#内容缓存)
- 从源码构建
  - [安装依赖项](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#安装依赖项)
  - [克隆NGINX GitHub仓库](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#克隆nginx-github仓库)
  - [配置构建参数](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#配置构建参数)
  - [编译](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#编译)
  - [二进制文件位置与安装](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#二进制文件位置与安装)
  - [运行与测试安装的二进制文件](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#运行与测试安装的二进制文件)
- [提问与问题报告](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#提问与问题报告)
- [代码贡献](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#代码贡献)
- [其他帮助资源](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#其他帮助资源)
- [更新日志](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#更新日志)
- [许可证](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#许可证)

------

# 工作原理

NGINX是预编译软件，为所有主流操作系统和Linux发行版提供二进制包。完整兼容系统列表请参见[测试过的OS与平台](https://nginx.org/en/#tested_os_and_platforms)。

> [!重要提示]
>  虽然几乎所有主流Linux发行版都附带社区版NGINX，但我们强烈建议使用本仓库的[官方软件包](https://nginx.org/en/linux_packages.html)或源码。这能确保您使用最新版本，包含最新功能集、修复和安全补丁。

## 模块

NGINX由独立模块组成，每个模块通过提供额外可配置功能扩展核心能力。完整官方模块列表参见NGINX文档底部的[模块参考](https://nginx.org/en/docs/)。

模块可分为**静态模块**和**动态模块**：

- **静态模块**：编译时绑定，直接集成到二进制文件中
- **动态模块**：独立编译，可在运行时加载（详见[动态模块](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#动态模块)）

> [!技巧]
>  通过以下命令查看二进制文件包含的静态模块：
>
> ```
> nginx -V
> ```
>
> 静态模块集成方法参见[配置构建参数](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#配置构建参数)。

## 配置

NGINX通过文本配置文件实现高度灵活性，配置文件采用"[指令](https://nginx.org/en/docs/dirindex.html)"参数。完整配置结构说明详见[配置文件结构](https://nginx.org/en/docs/beginners_guide.html#conf_structure)。

> [!注意]
>  可用指令集取决于NGINX发行版包含的[模块](https://tencent.yuanbao/chat?from=launch&conversation=afcecbcc-2055-4fe5-ba18-c67cf37b207a&project_id=&project_name=#模块)。

## 运行时

NGINX采用多进程架构突破操作系统限制，包含：

- **Master进程**：管理Worker进程，读取并解析配置文件
- **Worker进程**：处理实际数据（如HTTP请求），数量可通过[worker_processes](https://nginx.org/en/docs/ngx_core_module.html#worker_processes)指令配置

> [!技巧]
>  进程间通过共享内存同步数据。因此许多指令需分配共享内存区（如配置[速率限制](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html#limit_req)时需在[公共内存区](https://nginx.org/en/docs/http/ngx_http_limit_req_module.html#limit_req_zone)跟踪客户端访问）。

------

# 下载与安装

## 稳定版与主线版二进制包

提供两种版本：

- **稳定版(Stable)**：含关键修复的后向兼容版本
- **主线版(Mainline)**：基于[master分支](https://github.com/nginx/nginx/tree/master)的最新功能版
   版本选择指南参见[官方文档](https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/#choosing-between-a-stable-or-a-mainline-version)。

## Linux二进制安装流程

通过系统包管理器安装：

1. 添加官方仓库（[详细步骤](https://nginx.org/en/linux_packages.html)）
2. 使用包管理器安装（如`apt install nginx`）

### 升级

后续升级可通过相同包管理器完成。

## FreeBSD安装流程

安装指南详见：https://nginx.org/en/docs/install.html

## Windows可执行文件

主线和稳定版Windows可执行文件请在[NGINX下载页](https://nginx.org/en/download.html)获取。注意当前Windows版本为概念验证阶段，仅建议用于开发测试（详见[Windows版说明](https://nginx.org/en/docs/windows.html)）。

## 动态模块

自NGINX 1.9.11起支持[动态模块](https://nginx.org/en/docs/ngx_core_module.html#load_module)。动态模块可在NGINX核心安装后单独加载，[官方动态模块包](https://nginx.org/en/linux_packages.html#dynmodules)与核心包同源。

> [!技巧]
>  [NGINX JavaScript (njs)](https://github.com/nginx/njs)是热门动态模块，支持用JavaScript语法扩展功能。

> [!重要提示]
>  动态模块也可编译为静态模块集成。

------

# NGINX快速入门

基础教程请参阅：[初学者指南](https://nginx.org/en/docs/beginners_guide.html)。

## 安装SSL证书与启用TLS加密

HTTPS配置指南：[配置HTTPS服务器](https://nginx.org/en/docs/http/configuring_https_servers.html)。

## 负载均衡

快速配置指南：[使用NGINX作为HTTP负载均衡器](https://nginx.org/en/docs/http/load_balancing.html)。

## 速率限制

核心概念解析参见博客：[NGINX速率限制技术](https://blog.nginx.org/blog/rate-limiting-nginx)。

## 内容缓存

配置指南：[NGINX内容缓存技术详解](https://blog.nginx.org/blog/nginx-caching-guide)。

------

# 从源码构建

## 安装依赖项

以Debian/Ubuntu系统为例（`apt`包管理器）：

```
# 更新软件源
sudo apt update

# 安装编译工具
sudo apt install gcc make

# 核心依赖库
sudo apt install libpcre3-dev zlib1g-dev

# 启用TLS需额外安装
sudo apt install libssl-dev
```

## 克隆NGINX GitHub仓库

```
git clone https://github.com/nginx/nginx.git
```

## 配置构建参数

在源码根目录执行：

```
auto/configure
```

> [!重要提示]
>  无参数配置将使用默认选项，完整参数参见[配置文档](https://nginx.org/en/docs/configure.html)。

## 编译

生成Makefile后执行：

```
make
```

## 二进制文件位置与安装

编译产物路径：`<源码目录>/objs/nginx`
 安装命令：

```
sudo make install
```

默认安装路径：`/usr/local/nginx/`

## 运行与测试安装的二进制文件

启动命令：

```
sudo /usr/local/nginx/sbin/nginx
```

测试命令：

```
curl localhost
```

预期输出开头为：

```
<!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
```

------

# 提问与问题报告

- 技术讨论：[GitHub Discussions](https://github.com/nginx/nginx/discussions)
- 问题报告：[GitHub Issues](https://github.com/nginx/nginx/issues)

# 代码贡献

贡献指南详见：[CONTRIBUTING.md](https://tencent.yuanbao/CONTRIBUTING.md)

# 其他帮助资源

- 社区博客：[NGINX社区博客](https://blog.nginx.org/)
- 官方门户：[nginx.org](https://nginx.org/)

# 更新日志

版本更新记录：[CHANGES](https://nginx.org/en/CHANGES)

# 许可证

[类似BSD的2条款许可证](https://tencent.yuanbao/LICENSE)

------

文档主站：

（注：所有代码块、URL链接及技术术语均按原始文档保留，Markdown语法结构完整转换，特殊提示框转换为中文强调句式）