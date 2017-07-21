---
layout: post
title: 自动化IT工具ansible学习心得
categories: Linux
description: 自动化IT工具ansible学习心得
keywords: ansible,linux,IT
---

最近学习了一款自动化IT工具——ansible，因为发现一些错误在网上很难搜到解决方案，只能自己摸索，于是把自己遇到的问题总结了一遍。

# 心得

## 安装

Ansible是基于Python开发的，所以本机需要有python环境，然后只需执行`pip install ansible`就可以安装了
 
  > pip安装方法 `python get-pip.py` 
  
安装完成后可以通过ansible -h 命令来确认是否安装成功
  
## 配置SSH key

因为Ansible是通过ssh（安全外壳协议）进行通讯的，所以我们先生成ssh key。

### 检查SSH keys是否存在

输入下面的命令，如果有文件id_rsa.pub 或 id_dsa.pub，则直接进入步骤3将SSH key上传到需要部署的服务器中，否则进入第二步生成SSH key

```
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

### 生成SSH key

```
ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key using the provided email
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home_path/.ssh/id_rsa):
```

### 上传SSH key

 > 将本地主机的~/.ssh/id_rsa.pub的内容依次添加到远程服务器的~/.ssh/authorized_keys 文件中，
 并执行chmod 600 ~/.ssh/authorized_keys命令。添加完成后，可依次通过ssh username@ip进行测试，
 直到可以免密登录即可。

## 配置hosts

一般通过pip安装的ansible 都在 /etc下，如果不在，可使用 whereis命令查找。而我们需要配置的
hosts文件路径就应该是 `/etc/ansible/hosts`，根据官网的规则，没有组的放在最上面，有组的放在对应组名下。

配置好hosts文件后，我们还需要测试下是否能ping通，这里可以采用这条命令

```
ansible all -m ping
```

如果报错，可以加上 -vvvv查看详细报错原因

  > 值得注意，ansible默认是用你当前用户去指定机器上操作，比如你本地用户叫kanye，线上用户叫root，就会出现Connection refused错误

## 执行

```
ansible test -a "/bin/echo hello" -u root
```

这样做就成功的在test分组的机器上全部执行 echo hello 命令了

  > ansible默认是在当前目录下读取hosts文件的，所以请在/etc/ansible下执行命令，或修改配置文件，使他读取指定位置

## Playbooks

### 学习[YAML 语法](http://ansible-tran.readthedocs.io/en/latest/docs/YAMLSyntax.html)

因为Playbooks是基于yaml的，所以要想自定义一个Playbooks,需要掌握ymal语法。

### 上[Ansible Galaxy](https://galaxy.ansible.com/)下载个别的人playbooks

Ansible Galaxy有很多别人写好的Playbooks，包括java、redis、mysql、php等等，所以如果没有特殊需求，可以考虑去Ansible Galaxy下一个。

```
ansible-galaxy install geerlingguy.java
```

比如我需要一个java的部署工具，就可以这样下载一份

然后根据他的readme，配置java文件地址

# 参考资料

1. [Ansible中文权威指南](http://www.ansible.com.cn/index.html)

2. [自动化IT工具ansible使用指南](https://zhuanlan.zhihu.com/p/25387801)