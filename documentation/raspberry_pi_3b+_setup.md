1. 下载ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img.xz镜像压缩文件，解压得到ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img镜像文件；

2. Windows下用SDFormatter软件格式化SD卡；

3. Windows下用Win32DiskImager软件把ubuntu-mate-16.04.2-desktop-armhf-raspberry-pi.img镜像文件烧到SD卡；

4. 烧写完后，删除所有文件只保留cmdline.txt文件；

5. 把“raspbian的boot分区的文件”（除了cmdline.txt，其余全部复制）全部复制到“ubuntu-mate-16.04.2的boot分区的文件”；

6. 把SD卡插入树莓派3B+启动，会发现彩虹屏没有了，但是这时候鼠标和键盘无法使用，继续看下一步；

7. 取下SD卡，把SD插入电脑，挂载SD到Ubuntu，把刚才复制的以下文件夹复制到Ubuntu mate的主分区对应的路径下；

```
/lib/modules/4.9.80-v7+ (主分区)

/lib/firmware/brcm/ (主分区)
```

8. 把SD卡插入树莓派3B+启动，会发现彩虹屏没有了，鼠标键盘都可以使用了；

9. 完毕；
