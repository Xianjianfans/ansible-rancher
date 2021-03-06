# ansible-rancher
init os env and install rancher single

适用centos7x版本

#### 说明：k8s环境init playbook
- ntp同步
- selinux
- rancher用户
- firewalld
- kernel参数优化
- sysctl
- docker 18.09
- docker参数优化
- 锁定docker-ce版本
- 安装rancher单master节点

#### 须知
如自己环境内网有dns服务，修改/roles/common/files/resolv.conf内容为你本地dns服务器

#### 使用方法

git clone 文件至本地

当前目录建立host文件，例如test.host：
```
[master]
192.168.1.1

[node]
192.168.1.2
192.168.1.3
```
#### 执行playbook命令：

三台节点都做初始化操作,host=all,指对所有主机执行
```
ansible-playbook docker.yml -i test.host --extra "host=all name=rancher"
```
master节点安装rancher，这里使用了阿里云镜像源，写死安装2.4.3版本，具体可以参考rancherlabs公众号文章，如何优雅的在中国使用rancher
```
ansible-playbook rancher.yml -i 1.txt --extra "host=master name=rancher"
```

