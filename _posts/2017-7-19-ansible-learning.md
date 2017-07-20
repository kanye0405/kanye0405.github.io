---
layout: post
title: 自动化IT工具ansible学习心得
categories: Linux
description: 自动化IT工具ansible学习心得
keywords: ansible,linux,IT
---

# 心得

## 安装

Ansible是基于Python开发的，所以本机需要有python环境，然后只需执行`pip install ansible`就可以安装了
 
  > pip安装方法 `python get-pip.py` 
  
安装完成后可以通过ansible -h 命令来确认是否安装成功
  
## 配置SSH key

因为Ansible是通过ssh（安全外壳协议）进行通讯的，所以我们先生成ssh key。

1. 检查SSH keys是否存在

输入下面的命令，如果有文件id_rsa.pub 或 id_dsa.pub，则直接进入步骤3将SSH key上传到需要部署的服务器中，否则进入第二步生成SSH key

```
ls -al ~/.ssh
# Lists the files in your .ssh directory, if they exist
```

2. 生成SSH key

```
ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key using the provided email
Generating public/private rsa key pair.
Enter file in which to save the key (/your_home_path/.ssh/id_rsa):
```

3. 上传SSH key

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

  > 值得注意，ansible默认是用你当前用户去指定机器上操作，比如你本地用户叫kanye，线上用户叫root，就会出现Permission Denied

## 执行

```
ansible test -a "/bin/echo hello" -u root
```

这样做就成功的在test分组的机器上全部执行 echo hello 命令了

## playbook

未完待续

# 参考资料

1. [Ansible中文权威指南](http://www.ansible.com.cn/index.html)

2. [自动化IT工具ansible使用指南](https://zhuanlan.zhihu.com/p/25387801)