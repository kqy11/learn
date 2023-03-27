更新yum包：
  进入yum源配置文件夹
  cd /etc/yum.repos.d
  更改repo文件
  执行yum源更新命令
    yum clean all
    yum makecache
    yum -y update
