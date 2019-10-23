**参考文章**
1. [Linux非root用户登录](https://blog.csdn.net/qq_44755953/article/details/96187265)
2. [SSH-keygen用法](https://www.cnblogs.com/yanglang/p/9563496.html)

**具体解析**
1. 先通过SSH-SSH-keygen制作ssh key
2. 将制作好的ssh key放置到服务器上。地址：登录用户名的默认目录下的.ssh(cd ~)
3. 可以通过修改vim /etc/ssh/sshd_config文件内容，来禁止密码登录或者root权限登录。

**具体命令**
1. ssh-keygen -t rsa -b 3072 直接生成ssh key(-t 类型，默认是rsa -b 秘钥长度，默认是2048)，默认生成的文件名称为
id_rsa(私钥)  id_rsa.pub(公钥，需要放置到服务器上的~.ssh/authorized_keys文件内)
2. service sshd restart 重新启动sshd服务，使修改的/etc/ssh/sshd_config文件生效。
