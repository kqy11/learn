命令

获取当前系统占用内存最高的前10个进程
  ps aux|head -1;ps aux|sort -rn -k4|head -10
  第1句主要是为了获取标题信息。
  head: -N可以指定显示的行数，默认显示10行。
  第2个命令是一个输出加排序组合，ps参数的a指代all，表示所有的进程；u指代user id，就是执行该进程的用户ID；x指代显示所有程序，不以终端机来区分。
  接下来是sort命令：
  lr指代reverse，这里是指反向比较结果，输出时默认从小到大，反向后从大到小。
  ln指代numberic sort，根据其数值排序。
  lk代表根据哪一列进行排序。
  l数字3表示按照第3列排序。
  K4表示根据%MEM的数值进行由大到小的排序

显示cpu具体pid占用比例
  perf record -a -g -p 9 --sleep 30 #9为高ksoftirqd的pid
  perf report --sort=comm --stdio
