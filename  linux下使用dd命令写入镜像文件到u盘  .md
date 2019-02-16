1、使用 df -h​ ,查看一下当前各个磁盘

```
ser@host ~/ $ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       119G   79G   34G  70% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            7.8G   12K  7.8G   1% /dev
tmpfs           1.6G  1.1M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            7.9G  1.5M  7.9G   1% /run/shm
none            100M  3.7M   97M   4% /run/user
/dev/sdb1       2.0G  0.0G  2.0G   0% /media/user/LABEL
```

2、如果你的u盘被分成多个分区了，你需要全部umount， user@host ~ $ sudo umount /dev/sdb1 

4、使用dd命令将镜像写入刚才找到的分区，注意：不用写分区号。

```
sudo dd if=/home/jack/ubuntu.16.04.iso of=/dev/sdb bs=4M
```

小技巧：你可以在另外一个终端观察运行情况。

```
sudo watch kill -USR1 $(pgrep ^dd)
```

5、当刻录结束后，运行：

```
sync
```

该命令是检查一下，刻录是否运行完毕，当sync结束后，就可以安全的拔出u盘了。