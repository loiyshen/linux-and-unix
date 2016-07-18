# scp 命令

scp 可以在 2个 linux 主机间复制文件； 

命令基本格式： 
```
scp [可选参数] file_source file_target 
```

## 从 本地 复制到 远程 

### 复制文件： 

#### 命令格式：
```bash
// 格式1
// 指定了用户名，命令执行后需要再输入密码
// 指定了远程的目录，未指定远程文件名，所以文件名不变
scp local_file remote_username@remote_ip:remote_folder

// 格式2
// 指定了用户名，命令执行后需要再输入密码
// 指定了远程的目录和文件名，所以文件名会使用指定的文件名
scp local_file remote_username@remote_ip:remote_folder/remote_file

// 格式3
// 没有指定用户名，命令执行后需要输入用户名和密码
// 指定了远程的目录，未指定远程文件名，所以文件名不变
scp local_file remote_ip:remote_folder

// 格式4
// 没有指定用户名，命令执行后需要输入用户名和密码
// 指定了远程的目录和文件名，所以文件名会使用指定的文件名
scp local_file remote_ip:remote_folder/remote_file 
```

#### 例子：
```bash
scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music
scp /home/space/music/1.mp3 root@www.cumt.edu.cn:/home/root/others/music/001.mp3
scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music
scp /home/space/music/1.mp3 www.cumt.edu.cn:/home/root/others/music/001.mp3
```

### 复制目录：
#### 命令格式：
```bash
// 格式1
// 指定了用户名，命令执行后需要再输入密码
scp -r local_folder remote_username@remote_ip:remote_folder

// 格式2
// 没有指定了用户名，命令执行后需要再输入密码
scp -r local_folder remote_ip:remote_folder 
```

#### 例子：
```bash
scp -r /home/space/music/ root@www.cumt.edu.cn:/home/root/others/ 
scp -r /home/space/music/ www.cumt.edu.cn:/home/root/others/
// 上面 命令 将 本地 music 目录 复制 到 远程 others 目录下，即复制后有 远程 有 ../others/music/ 目录 
```



## 从 远程 复制到 本地 

从 远程 复制到 本地，只要将 从 本地 复制到 远程 的命令 的 后2个参数 调换顺序 即可；

#### 例如：
```bash
scp root@www.cumt.edu.cn:/home/root/others/music /home/space/music/1.mp3
scp -r www.cumt.edu.cn:/home/root/others/ /home/space/music/
```


## 可能有用的几个参数 : 
```
-v 和大多数 linux 命令中的 -v 意思一样 , 用来显示进度 . 可以用来查看连接 , 认证 , 或是配置错误
-C 使能压缩选项
-P 选择端口，注意 -p 已经被 rcp 使用
-4 强行使用 IPV4 地址
-6 强行使用 IPV6 地址
```
