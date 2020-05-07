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







# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "${PS1-}" ]; then
  if [ "${BASH-}" ] && [ "$BASH" != "/bin/sh" ]; then
    # The file bash.bashrc already sets the default PS1.
    # PS1='\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
      . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi
#java_home
JAVA_HOME=/usr/jdk/jdk1.8
      PATH=$JAVA_HOME/bin:$PATH
      CLASSPATH=.:$JAVA_HOME/lib/dt.jar:
      $JAVA_HOME/lib/tools.jar
      export JAVA_HOME
      export PATH
      export CLASSPATH







运行命令：source /etc/profile 重新加载profile使配置立即生效