nginx
  资料
  Nginx安装及配置文件nginx.conf详解https://blog.csdn.net/shenxiaomo1688/article/details/105858118
  
  
  1、安装Nginx
  
  2、Nginx的配置文件结构
    Nginx的配置文件nginx.conf位于其安装目录的conf目录下。例如：/etc/nginx/nginx.conf
    nginx.conf由多个块组成，最外面的块是main，main包含Events和HTTP，HTTP包含upstream和多个Server，Server又包含多个location：
      main（全局设置）块设置的指令将影响其他所有设置；
      server（主机设置）块的指令主要用于指定主机和端口；
      upstream（负载均衡服务器设置）指令主要用于负载均衡，设置一系列的后端服务器；
      location（URL匹配特定位置的设置）块用于匹配网页位置。  
    
  3、Nginx的全局配置
  user nobody nobody;
  worker_processes 2;
  error_log logs/error.log notice;
  pid logs/nginx.pid;
  worker_rlimit_nofile 65535;
 
  events{
  use epoll;
  worker_connections 65536;
  }
  每个配置选项的含义解释如下：
    user是个主模块指令，指定Nginx Worker进程运行用户以及用户组，默认由nobody账号运行。
    worker_processes是个主模块指令，指定了Nginx要开启的进程数。每个Nginx进程平均耗费10M~12M内存。建议指定和CPU的数量一致即可。
    error_log是个主模块指令，用来定义全局错误日志文件。日志输出级别有debug、info、notice、warn、error、crit可供选择，其中，debug输出日志最为最详细，而crit输出日志最少。
    pid是个主模块指令，用来指定进程pid的存储文件位置。
    worker_rlimit_nofile用于绑定worker进程和CPU， Linux内核2.4以上可用。
