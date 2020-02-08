# vSphere go命令行管理工具govc

# 一、简介

VMware vSphere APIs (ESXi and/or vCenter)的go语言客户端

- [govc](https://github.com/vmware/govmomi/blob/master/govc) - vSphere CLI
- [vcsim](https://github.com/vmware/govmomi/blob/master/vcsim) - vSphere API mock framework
- [toolbox](https://github.com/vmware/govmomi/blob/master/toolbox) - VM guest tools framework

支持的ESXi / vCenter版本：

-  ESXi / vCenter 6.0, 6.5 , 6.7 (5.5和5.1版本功能部分支持, 但官方不再支持)

**GitHub地址**：https://github.com/vmware/govmomi

**govc下载地址**：https://github.com/vmware/govmomi/releases

**govc使用手册**：https://github.com/vmware/govmomi/blob/master/govc/USAGE.md

# 二、安装配置

## 1、安装

在[govc下载地址](https://github.com/vmware/govmomi/releases)下载对应平台的二进制包

```bash
curl -L $URL_TO_BINARY | gunzip > /usr/local/bin/govc
chmod +x /usr/local/bin/govc
```

MacOS对应`govc_darwin_amd64.gz`

## 2、配置

govc是通过设置环境变量进行配置的。

- `GOVC_URL`：ESXi或vCenter实例的地址

  默认协议`https` ，URL路径为 `/sdk` 。可在URL中设置用户名密码，例如： `https://user:pass@host/sdk`.

  如果用户名密码中包含特殊字符( `\`, `#` , `:`)，可以在 `GOVC_USERNAME` ， `GOVC_PASSWORD` 单独设置用户名密码。

- `GOVC_USERNAME`：用户名

- `GOVC_PASSWORD`：密码

- `GOVC_TLS_CA_CERTS`：指定CA证书

  ```bash
  $ export GOVC_TLS_CA_CERTS=~/.govc_ca.crt
  # 多证书设置
  $ export GOVC_TLS_CA_CERTS=~/ca-certificates/bar.crt:~/ca-certificates/foo.crt
  ```

- `GOVC_TLS_KNOWN_HOSTS`：指定验证证书的指纹

  ```bash
  $ export GOVC_TLS_KNOWN_HOSTS=~/.govc_known_hosts
  $ govc about.cert -u host -k -thumbprint | tee -a $GOVC_TLS_KNOWN_HOSTS
  $ govc about -u user:pass@host
  ```

- `GOVC_TLS_HANDSHAKE_TIMEOUT`: TLS握手的超时时间

- `GOVC_INSECURE`：关闭证书验证

  ```bash
  export GOVC_INSECURE=1
  ```

- `GOVC_DATACENTER`：

- `GOVC_DATASTORE`：

- `GOVC_NETWORK`：

- `GOVC_RESOURCE_POOL`：

- `GOVC_HOST`：

- `GOVC_GUEST_LOGIN`：

- `GOVC_VIM_NAMESPACE`：

- `GOVC_VIM_VERSION`：

以上变量可在`~/.zshrc或/etc/profile或~/.bashrc`中设置，同时可使用`govc env`查看设置。

# 三、常用命令

具体命令详解可查看文档：https://github.com/vmware/govmomi/blob/master/govc/USAGE.md

## 查看所有VM

$$

$$

```bash
govc find . -type m
```

## VM电源的开启与关闭

```bash
# 开启VM电源
govc vm.power -on -M VM_Name
# 关闭VM电源
govc vm.power -off -M VM_Name
```







