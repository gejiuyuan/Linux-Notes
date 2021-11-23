## ls

- 英文原意：list

- 命令所在路径：/bin/ls

- 执行权限：所有用户

- 功能：显示目录文件

- 语法：ls [选项] [文件或目录]

- 用法：

  ```
  //显示所有文件（all），包括隐藏文件
  ls -a
  
  //详细信息（long，长格式信息）显示，如文件大小、最后一次修改日期、拥有修改权限的用户名等
  ls -l
  
  //查看目录属性
  ls -d
  
  //ls -a和ls -l简写
  ls -al
  
  //显示详细信息，同时考虑人性化（human，如让文件大小显示K、M等单位，而不是默认不显示的B）
  ls -lh
  
  //只查看该目录的详细信息，而不是该目录下的所有文件的详细信息
  ls -ld
  
  //查看根目录文件
  ls /
  
  //
  ls -i
  ```
  
  > 1、隐藏文件：设计初衷是告诉用户这是一个系统级文件，我们不要乱动它。特别的，不同于windows，Linux系统规定，以.开头的文件即被视为隐藏文件。换言之，如果想要让文件隐藏，只需要将其以.开头命名即可
  >
  > 2、Linux中，每个文件就把用户分成了三类：所有者（user，一个文件有且只有一个）、所属组（group，一个文件有且只有一组）、其它人（other）
  
- 示例：

  如图所示是ls -al的结果

  ![](./img/ls命令.png)

  列表从左至右的含义是：

  - 综合特性描述：

    - 第一项：文件类型，如：二进制文件（-）、目录（d）和软链接文件（l），以及其它大多用不到的文件类型。

    - 后九项：

      | u（user） | g（group） | o（other） |
      | :-------: | :--------: | :--------: |
      |  所有者   |   所属组   |   其他人   |
      |    r读    |    w写     |   x执行    |

      ```
      //一个文件夹目录
      //文件权限：所有者-->读、写、执行；所属组-->读、执行；其他人-->读、执行
      drwxr-xr-x.
      ```

  - 引用计数：表示此文件曾经被调用或引用过多少次

  - 文件所有者

  - 文件所属组

  - 文件大小：默认单位字节

  - 文件最后一次修改时间

  - 文件名

## mkdir

- 命令名称：mkdir

- 原意：make directory

- 命令所在路径：/bin/mkdir

- 执行权限：所有用户

- 语法：mkdir -p [目录名]

- 功能描述：创建新目录。-p表示递归创建

  ```
  //此时如果有/tmp目录，但是没有japan，而我们想创建/tmp/japan/boduo目录，则必须使用-p选项
  mkdir -p /tmp/japan/boduo
  //可创建多个目录
  mkdir /tmp/japan/longze /tmp/japan/cangjing
  ```



## cd

- 原意：change directory

- 命令所在路径：shell内置命令

- 执行权限：所有用户

- 语法：cd [目录]

- 功能描述：切换名录

  ```
  //回到上级目录
  cd ..
  ```

## pwd

- 原意：print working directory
- 所在路径：/bin/pwd
- 执行权限：所有用户
- 语法：pwd
- 功能描述：显示当前目录

## rmdir

- 原意：remove empty directory
- 所在路径：/bin/rmdir
- 执行权限：所有用户
- 语法：rmdir [目录名]
- 功能描述：删除空目录

## cp

- 原意：copy

- 所在路径：/bin/cp

- 执行权限：所有用户

- 语法：

  ```
  cp -rp [原文件或目录] [目标目录]
  cp -r 复制目录
  cp -p 保留文件属性（比如复制一个文件到新目录，用ls -l [新目录的该文件]时，上一次修改时间将原封不变）
  ```

- 功能描述：复制文件或目录

  ```
  //复制/tmp/haha目录到/root下。
  //注意：复制目录必须使用-r选项，而复制文件则不需要
  cp -r /tmp/haha /root
  
  //复制/tmp/aa.txt到/root下
  cp /tmp/aa.txt /root
  
  //复制/tmp/bb.txt和/tmp/cc.txt到/root/dev目录下
  cp /tmp/bb.txt /tmp/cc.txt /root/dev
  ```

## mv

- 原意：move

- 所在路径：/bin/mv

- 执行权限：所有用户

- 语法：mv [原文件或目录] [目标名录]

- 功能描述：剪切文件、改名

  ```
  //移动/tmp/haha目录到/root下
  mv /tmp/haha /root
  
  //修改本目录下的haha文件夹名字为baba
  mv haha baba
  ```



## touch

- 原意：remove

- 所在路径：/bin/touch

- 执行权限：所有用户

- 语法：touch [文件名]

- 功能描述：创建空文件

  ```
  //在文本录下创建haha.list
  touch haha.list
  
  //在根目录创建haha.list文件
  touch /root/haha.list
  
  //创建haha baba两个文件
  touch haha baba
  
  //创建一个带空格的文件名——haha baba
  touch "haha baba"
  ```

## rm

- 原意：remove

- 所在路径：/bin/rm

- 执行权限：所有用户

- 语法：

  ```
  rm -rf [文件或目录]
  rm -r 删除目录
  rm -f 强制删除（不会提示确认信息）
  ```

- 功能描述：删除文件或目录

  ```
  // 删除hello.txt文件
  rm hello.txt
  
  // 删除haha目录
  rm -d haha
  rm -r haha
  ```

## cat

- 所在路径：/bin/cat

- 执行权限：所有用户

- 语法：

  ```
  cat [文件]
  cat -n [文件] --> 显示行号
  ```

- 功能描述：显示文件内容

  ```
  cat /etc/issue 
  cat -n /etc/services
  ```

## tac

- 所在路径：/usr/bin/tac

- 执行权限：所有用户

- 语法：tac [文件]

- 功能描述：反过来显示文件内容

  ```
  tac /etc/issue
  ```

  但是cat和tac都不适合浏览内容比较长的文件，视觉效果会不好（shell命令行可能只会显示内容的最后一页）。此时建议使用more命令查看文件

## more

- 所在路径：/bin/more

- 执行权限：所有用户

- 语法：

  ```
  more [文件名]
  	 (空格)或f 一页一页往下翻
  	（Enter） 一行一行往下翻
  	 q或Q 退出
  ```

- 功能描述：分页显示文件内容（只能向下翻页）

  ```
  more /etc/services
  ```

## less

- 所在路径：/bin/less

- 执行权限：所有用户

- 语法：

  ```
  less [文件名]
  	 (空格)或f 一页一页往下翻
  	（Enter） 一行一行往下翻
  	 q或Q 退出
  	 pgUp 一页一页往上翻
  	 上箭头 一行一行往上翻
  	/ [内容] 搜索关键字。如果当页没有，可再摁n（即next），去下一页查找
  ```

- 功能描述：分页显示文件内容（能向上也能往下翻页）

  ```
  less /etc/services
  ```

## head

- 所在路径：/usr/bin/head

- 执行权限：所有用户

- 语法：head -n [文件名]

- 功能描述：显示文件前面几行，-n指定行

  ```
  //显示该文件内容（默认显示前10行）
  head /etc/haha.txt
  
  //显示该文件的前20行
  head -n 20 /etc/haha.txt
  ```

## tail

- 所在路径：/usr/bin/tail

- 执行权限：所有用户

- 语法：tail -n [文件名]

- 功能描述：显示文件后面几行，-n 指定行数 ，-f 动态显示文件末尾内容（比如远程操作后的日志文件内容自动更新）

  ```
  //显示该文件内容（默认显示后10行）
  tail /etc/haha.txt
  
  //显示该文件的后20行
  tail -n 20 /etc/haha.txt
  ```



## ln

- 原意：link

- 所在路径：/bin/tail

- 执行权限：所有用户

- 语法：

  ```
  ln -s [原文件] [目标文件]
  ln -s 创建软链接
  ```

- 功能描述：生成链接文件

  ```
  //
  ls -s
  ```





### 二、权限管理命令



### 三、文件搜索命令



### 四、帮助命令



### 五、用户管理命令



### 六、压缩解压命令



### 七、网络命令



### 八、关机重启命令

