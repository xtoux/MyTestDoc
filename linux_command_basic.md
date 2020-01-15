[toc]

###### 1.命令快速入门url



[Linux Tools Qucik Tutorial](https://linuxtools-rst.readthedocs.io/zh_CN/latest/)

[Github地址](https://github.com/me115/linuxtools_rst)

###### 2.常用命令内容分8个部分

- 历史及帮助

- 文件及目录管理

- 文本处理

- 磁盘管理

- 进程管理

- 性能监控

- 网络工具

- 用户管理工具

  

###### 3.命令使用

**3.1:帮助命令man**

各章节内容: 1.用户命令2.系统调用或内核函数 3.库函数 4.与设备有关的信息 5.文件格式描述 6.游戏7.其他 8.系统管理 9.内核

如何用快捷键看文档: 

​    向下键:向下滚动一行 

​    向上键:向上滚动一行 

​    回车键:向下滚动一行 

​    空白键:向下翻一页

​    Page Down:向下翻一页

​    Page Up:向上翻一页

​    Home:到第一页

​    End:到最后一页

​    b:向前翻一页 

​    d:向后翻半页

​    q:退出 

​    /字符串:向下搜索“字符串” 

​    ?字符串:向上搜索“字符串”

​    n:查找下一个

​     N:查找前一个

- 在只记得部分命令关键字的场合，我们可通过man -k来搜索；

- 需要知道某个命令的简要说明，可以使用whatis；而更详细的介绍，则可用info命令；

- 查看命令在哪个位置，我们需要使用which；

- 而对于命令的具体参数及使用方法，我们需要用到强大的man；

  

**帮助：**

`whatis printf`

`info command`

`man 2 mkdir`

`man -k keyword`

**查看路径**

`which python`

`which make`

`whereis python`

`whereis mysql`

***

**3.2:文件及目录管理命令**

<u>3.2.1[创建和删除]</u>

- 创建：mkdir

- 删除：rm

- 删除非空目录：rm -rf file目录

- 删除日志 rm *log (等价: $find ./ -name “*log” -exec rm {} ;)

- 移动：mv

- 复制：cp (复制目录：cp -r )

  ***

  **touch**

  1. 创建一个文件

  ​                `touch testfile`

  2. 修改时间戳为当前时间

  ​                 `touch testfile` 

  3. 进阶

  ​                  -a -m -t

  

  **mkdir**

  1. 创建一个空目录 

     ​    `mkdir testdir`
  
2. 递归创建多个目录
          `mkdir -p testdir1/testdir2`

  **rm**

  1. 删除一个或多个文件 

     ​    `rm testfile1 testfile2`
  
2. 删除一个或多个目录
         `rm -r testdir1 testdir2`
  
3. 强制删除文件/目录
         `rm -rf testfile testdir`

  注意:千万不要运行 rm -rf /*

  **mv**
  
1. 移动文件/目录
      `mv testfile.txt testdir`
  
  2. 更改文件名
      `mv testfile1.txt testfile2.txt`
3. 进阶
      -i -f -b

  

  **cp**

  
  
1. 复制文件/目录
     `cp file1.txt file2.txt `

     `cp -r dir1 dir2`

  ​                  ps: dir2如果已经存在，则dir1将被复制到dir2目录下。

  ​                  如果dir2不存在，则dir1将复制成dir2

     2. 进阶

        -a -i -v

  
  
  <u>3.2.2 目录切换</u>
  
  **cd**
  
     . 当前目录，
     .. 上一层目录。
     cd 进入用户主目录;
     cd ~ 进入用户主目录;
     cd - 返回进入此目录之前所在的目录; cd .. 返回上级目录
     cd ../.. 返回上两级目录;
  
  **pwd**
  
  查看当前所在路径
  
  
  
  <u>3.2.3 列出目录项</u>
  
  **ls**
  
  1. 列出当前目录所有文件 
  
     `ls`
  
  2. 列出当前目录所有文件(包括隐藏文件) 
  
     `ls -a`
  
  3. 以列表形式列出当前目录所有文件(包括隐藏文件) 
  
     `ls-l --> ll`
  
  4. 以易于人类阅读形式列出当前目录所有文件
  
      `ls -lh`
  
  5. 进阶
      -r -t -i
  
  **tree**
  
  ​    以树形显示目录的文件架构
  
  ​         `tree`
  
  ​         `tree dir`
  
  如果出现乱码，alias tree = 'tree --charset ASCII'就可以了
  
  <u>3.2.2 权限及所有者</u>
  
  <img src="/Users/tuoxia/Library/Application Support/typora-user-images/image-20200115225331126.png" alt="image-20200115225331126" style="zoom:30%;" />
  
  **chown**
  
  ​    更改文件所有者
  ​       chown [-R] 所有者 文件或目录 
  
  ​       chown [-R] 所有者:所属组 文件或目录
  
  **chgrp**
  
  修改文件(或目录)的所属组
   chgrp [-R] 所属组 文件名(目录名)
  
  **chmod**
  
  1. 使用**数字**修改文件权限
  
     ​     `chmod 777 file`
  
     2.使用**字母**修改文件权限
  
     ​      u-user, g-group, o-other, a-all
  
  ​                        `chmod a+w file`
  ​                        `chmod u=rwx,go=rx .bashrc`
  
  <img src="/Users/tuoxia/Library/Application Support/typora-user-images/image-20200115225718686.png" alt="image-20200115225718686" style="zoom:33%;" />
  
  
  
  
  
  **3.3  文本处理命令**
  
  **cat**
  
  ​    cat不是猫，是单词concatenate的缩写，代表“连接”
  
  1. 在终端查看文本内容
  
     `cat file.txt`
  
  2. 从键盘创建一个文件
  
     `cat > file.txt`
  
  3. 将几个文件合并为一个文件
  
     `cat file1.txt file2.txt > file.txt`
  
  4. 进阶
  
     -n -b -s -v
  
  **more**
  
  ​    基本操作
  ​         q:退出 more
  
  ​         空格键:向下滚动一屏 
  
  ​         b:返回上一屏 
  
  ​         回车:向下滚动一行
  
  1. 分页显示文本文件内容 
  
     `more file.txt`
  
  2. 通过管道分页显示结果 
  
     `ll /etc | more`
  
  3. 进阶
      +n -n +/pattern -s -u
  
     
  
  **less**
  
  ​       基本操作 与man命令相同(实际上man命令的结果正是调用了less命令)
  
  1. 分页显示文本文件内容 
  
     `less file.txt`
  
  2. 通过管道分页显示结果 
  
     `ll /etc | less`
  
  3. 进阶
  
  
  
  **head**
  
  ​    显示文本文件前n行内容(默认显示前10行) 
  
  ​        `head -n 5 file.txt`
  
  **tail**
  
  1. 显示文件末尾内容
  
  ​                        `tail -n 5 file.txt` 
  
  2. 循环查看文件内容
  
  ​                        `tail -f file.txt`
  
  3. 从第5行开始显示文件
  
  ​                       `tail -n +5 file.txt`
  
  **sort**
  
  1. 按ASCII码升序排序 
  
  ​                      `sort file.txt`
  
  2. 排序并去除重复行
  
      `sort -u file.txt`
  
  3. 按ASCII码降序排序 
  
     `sort -r file.txt`
  
  **uniq**
  
  ​         删除重复行 
  
  ​             `uniq file.txt`
  
  
  
  
  
  **文本处理三剑客!! 每个命令单独拿出来都可以讲半小时!** 
  
  **grep**
  
  ​     命令格式
  
  ​          grep [option] pattern file 常用选项
  
  ​                -i 忽略大小写
  ​                -r 递归搜索文件
  ​               -n 标识结果所在的行数 
  
  ​               -s 不显示错误信息
  
  `grep -rins word file.txt`
  
  
  
  **sed**
  
  1. 文本的搜索并替换
      sed 's/text/replace_text/g' file.txt 默认替换后，输出替换后的内容，如果需要直接替换原文件,使用-i: sed -i 's/text/repalce_text/g' file
  
  2. 变量替换
      已匹配的字符串通过标记&来引用.
      echo this is en example | sed 's/\w\+/[&]/g'
  
  ​                               $>[this] [is] [en] [example]
  
  
  
  **awk**
  
  ​        命令格式
  ​                awk 'BEGIN{ statements } statements2 END{ statements }'
  
  例子
                  echo -e "line1\nline2" | awk 'BEGIN{print "start"} {print } END{ print "End" }'
  
  
  
  
  
  
  
  <u>3.4 磁盘管理命令</u>
  
  **df**
  
  ​    磁盘文件的可用空间 
  
  ​        df -h (h:human)
  
  **du**   
  
  1. 显示目录或者文件所占空间 
  
     `du (-h)`
  
  2. 显示指定文件所占空间
  
     `du file.txt`
  
  
  
  **tar**
  
  1. 压缩文件
      `tar zcvf file.tar.gz file1 file2`
  2. 解压文件
      `tar zxvf file.tar.gz`
  
  ​               -z 支持gzip属性的文件
  ​               -v 显示操作过程
  ​               -f 必须，使用档案名字，这个参数是最后一个参数，后面只能接档案名 -c 建立压缩档案
  ​               -x 解压
  
  
  
  <u>3.5 进程管理命令</u>
  
  **ps**
  
  ps命令是Process Status的缩写，用来列出系统中当前运行的那些进程 列出目前所有的正在内存当中的程序
       `ps aux`
  
  USER:该 process 属于那个使用者账号的
   PID :该 process 的号码
   %CPU:该 process 使用掉的 CPU 资源百分比
   %MEM:该 process 所占用的物理内存百分比
   VSZ :该 process 使用掉的虚拟内存量 (Kbytes)
   RSS :该 process 占用的固定的内存量 (Kbytes)
   TTY :该 process 是在那个终端机上面运作，若与终端机无关，则显示 ? STAT:该程序目前的状态，主要的状态有
  
  R :该程序目前正在运作，或者是可被运作
  
  S :该程序目前正在睡眠当中 (可说是 idle 状态)，但可被某些讯号 (signal) 唤醒。
  
  T :该程序目前正在侦测或者是停止了
  
  Z :zombie (疆尸) 程序
   START:该 process 被触发启动的时间
   TIME :该 process 实际使用 CPU 运作的时间 COMMAND:该程序的实际指令
  
  ​    `ps -ef`
  
  
  
  **top**
  
  top命令是Linux下常用的性能分析工具，能够实时显示系统中各个进程的资源占用状 况，类似于Windows的任务管理器。
  
  
  
  **kill**
  
  linux下向进程发送信号的命令
  
  ​             1. 列出所有命令名称
  
  ​                 `kill -l` 
  
  2. 杀死进程
  
  ​                  `kill –9 3268`
  
  
  
  **killall**
  
  ​    杀死指定名字的进程 
  
  ​            `killall vi`
  
  
  
  <u>3.6 网络工具</u>
  
  **ssh**
  
  1. 连接到远程主机
      `ssh name@remoteserver`
  
  2. 通过SSH运行远程shell命令
      `ssh name@10.203.138.129 “uname -a”`
  
  **wget**
  
  1. 使用wget下载单个文件 wget
  
  `https://dl.bintray.com/boostorg/release/1.71.0/source/boost_1_71_0.tar.bz2` 
  
  2. 断点续传
  
  `wget -c https://dl.bintray.com/boostorg/release/1.71.0/source/boost_1_71_0.tar.bz2`
  
  **scp**
  
  
  
  1. 上传文件
      `scp /home/alvin/file.txt root@10.203.138.129:/home/root`
  
  2. 下载文件
      `scp root@10.203.138.129:/home/root/file.txt /tmp`
  
  **ping**
  
  ```
   向指定的网络地址发送一定长度的数据包，按照约定，若指定网络地址存在的话，会返
  回同样大小的数据包
  ```
  
  1.  测试网络连通性 
  
     `ping baidu.com`
  
  2. ping指定次数
      `ping -c 5 baidu.com`
  
  
  
  <u>3.7 用户管理工具</u>
  
  **sudo**
  
  ​    以系统管理者的身份执行指令 
  
  ​        `sudo command`
  
  adduser: 会自动为创建的用户指定主目录、系统shell版本，会在创建时输入用户密码。 
  
  useradd:需要使用参数选项指定上述基本设置，如果不使用任何参数，则创建的用户无密 码、无主目录、没有指定shell版本。
   **useradd**
  
  sudo useradd -d "/home/alvin" -m -s "/bin/bash" alvin
  
  ​     -d “/home/alvin" :就是指定/home/alvin为主目录 
  
  ​    -m 就是如果/home/alvin不存在就强制创建
  ​     -s 就是指定shell版本
  
  
  
  **adduser**
  
  ​    `adduser user`
  
  **userdel**
  
  ​    删除用户 
  
  ​    `userdel -r user`
  
  **passwd**
  
  ​    更改密码 `passwd alvin`
  
  ​     （将其宿主目录和系统内与其相关的内容删除）
  
  **groupadd**
  
  ​    添加一个新组
  ​         `groupadd leader`
  ​     查询组
  ​         `cat /etc/group | grep leader`
  
  **groupmod**
  
  1. 更改组名
      `groupmod -n leaders leader`
  
  2. 更改组GID
      `groupmod -g 3000 leaders`
  
  **groupdel**
  
  ​    删除用户组 `groupdel leaders`
  
  
  
  4.vim命令
  
  3种模式切换
  
  <img src="/Users/tuoxia/Library/Application Support/typora-user-images/image-20200115234612783.png" alt="image-20200115234612783" style="zoom:33%;" />
  
  命令模式
  
  | 移动光标                               | h 或 ←   | 左移                                      |         |
  | -------------------------------------- | -------- | ----------------------------------------- | ------- |
  | 移动光标                               | l 或 →   | 右移                                      |         |
  | 移动光标                               | j 或↓    | 下移                                      |         |
  | 移动光标                               | k 或↑    | 上移                                      |         |
  | 移动光标                               | gg       | 光标移动文件开头                          |         |
  | 移动光标                               | G        | 光标移动到文件末尾                        |         |
  | 移动光标                               | 0        | 光标移动到行首                            |         |
  | 移动光标                               | $        | 光标移动到行尾                            |         |
  | 移动光标                               | 123G     | 跳转到第123行                             |         |
  | 删除（并不是真的删除，实际上是剪切）   | x        | 删除光标后一个字符,相当于 Del             |         |
  | 删除  （并不是真的删除，实际上是剪切） | X        | 删除光标前一个字符,相当于 Backspace       |         |
  | 删除  （并不是真的删除，实际上是剪切） | dw       | 删除光标开始位置的字,包含光标所在字符     |         |
  | 删除  （并不是真的删除，实际上是剪切） |          | 光标必须移动到删除单词的首字符上          |         |
  | 删除  （并不是真的删除，实际上是剪切） | d0       | 删除光标前本行所有内容,不包含光标所在字符 |         |
  | 删除  （并不是真的删除，实际上是剪切） | D（d$）: | 删除光标后本行所有内容,包含光标所在字符   |         |
  | 删除  （并不是真的删除，实际上是剪切） | dd       | 删除光标所在行                            |         |
  | 删除  （并不是真的删除，实际上是剪切） | n dd     | 删除指定的行数                            |         |
  | 撤销操作                               | u        | 一步一步撤销                              |         |
  | 撤销操作                               | Ctr-r    | 反撤销                                    |         |
  | 复制粘贴                               | yy       | 复制当前行,n yy 复制 n 行                 |         |
  | 复制粘贴                               | p (小写) | 在光标所在位置向下新开辟一行,粘贴         |         |
  | 复制粘贴                               | P (大写) | 在光标所在位置向上新开辟一行,粘贴         |         |
  | 可视模式                               | v        | 按字移动                                  |         |
  | 可视模式                               |          | 配合 h、j、k、l 使用，使用y复制选中内容   |         |
  | 查找操作                               | /hello   | 从光标所在位置向后查找 hello              | n下一个 |
  | 查找操作                               | N上一个  |                                           |         |
  | 查找操作                               | ?hello   | 从光标所在位置向前查找 hello              | n       |
  | 查找操作                               | N        |                                           |         |
  | 查找操作                               | #        | 在要查询的单词上使用 # 进行查找           |         |
  | 替换操作                               | r + 字符 | 替换当前字符                              |         |
  | 文本行移动                             | >>       | 文本行右移                                |         |
  | 文本行移动                             | <<       | 文本行左移                                |         |
  | 查看 Man Page                          | Shift-k  | 光标移动到函数上,Shift-k 光标移动到函数上 |         |
  | 查看 Man Page                          | 3Shift-k | 查看第三章的 ManPage                      |         |
  
  文本模式
  
  | 进入输入模式 | i    | 插入光标前一个字符    |
  | ------------ | ---- | --------------------- |
  | 进入输入模式 | I    | 插入行首              |
  | 进入输入模式 | a    | 插入光标后一个字符    |
  | 进入输入模式 | A    | 插入行未              |
  | 进入输入模式 | o    | 向下新开一行,插入行首 |
  | 进入输入模式 | O    | 向上新开一行,插入行首 |
  | 进入输入模式 | s    | 删除光标所在的字符    |
  | 进入输入模式 | S    | 删除当前行            |
  
  末行模式
  
  | 行跳转        | :123          |                              | 跳转到第123行                  |
  | ------------- | ------------- | ---------------------------- | ------------------------------ |
  | 替换          | 替换一行      | :s/abc/123                   | 将当前行中的第一个abc替换为123 |
  | 替换          | :s/abc/123/g  | 将当前行中的abc全部替换为123 |                                |
  | 替换          | 替换全部      | :%s/abc/123                  | 将所有行中的第一个abc替换为123 |
  | 替换          | :%s/abc/123/g | 将所有行中的abc全部替换为123 |                                |
  | 替换          | 替换指定行    | :10,30s/abc/123/g            | 将10-30行中的abc全部替换为123  |
  | 执行shell命令 | !             | 末行模式里输入!,后面跟命令   |                                |
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  











