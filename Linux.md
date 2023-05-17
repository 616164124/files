# Linux系统（CentOS 7(阿里云14)）

## 一、命令篇

### (1)sudo 命令  

xzm@ubuntu:~$  sudo

这样输入当前管理员用户密码就可以得到超级用户的权限。但默认的情况下5分钟root权限就失效了。

### (2)sudo -i

xzm@ubuntu:~$  sudo -i

通过这种方法输入当前管理员用户的密码就可以进到root用户。

### (3)如果想一直使用root权限，要通过su切换到root用户。

那我们首先要重设置root用户的密码：

xzm@ubuntu:~$  sudo passwd root

这样就可以设置root用户的密码了。

### (4)之后就可以自由的切换到root用户了

xzm@ubuntu:~$  su

输入root用户的密码即可。

su "king" 或者 exit回到用户权限

### (5)kill

在使用 kill -9 前，应该先使用 kill -15，给目标进程一个清理善后工作的机会。如果没有，可能会留下一些不完整的文件或状态（数据丢失或者终端无法恢复到正常状态等），从而影响服务的再次启动。



运行命令：source /etc/profile 重新加载profile使配置立即生效

