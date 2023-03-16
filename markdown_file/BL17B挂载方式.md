# BL17B线站Bluice收数据文件挂载方式



## Dataserver服务器文件夹建立

- 将ramdisk建联到dataInit文件夹。<br>

- data文件夹建联出文件夹link to data到dataInit文件夹，并将文件名改为ramdisk。<br>

![1](D:\work\markdown_file\1.jpg)

- 将dataInit/data软链接到根目录

  ```linux 
  ln -s /dataInit/data  /ramdisk
  ```

![2](D:\work\markdown_file\2.jpg)

```linux
cd ramdisk
mkdir data
cd data
mkdir bl17b1
#探测器过来的数据写到bl17b1文件夹
```

```linux
#修改exports文件夹
gedit /etc/exports
```

```gedit
/dataInit   10.30.63.*(rw,async)
/ramdisk   100.100.100.*(rw,insecure,async,all_squash)
```

## Bluice电脑文件夹建立

```linux
cd /data/data  #将data文件夹建立一个链接，放到ramdisk文件夹下
ramdisk文件夹目录下只有500_500和链接过来的data文件夹。
文件结构为
/ramdisk/data/bl17b1
```

## Pilatus2M服务器文件夹挂载

```linux
# 将Dataserver的ramdisk文件挂载过来
mount -a
```

