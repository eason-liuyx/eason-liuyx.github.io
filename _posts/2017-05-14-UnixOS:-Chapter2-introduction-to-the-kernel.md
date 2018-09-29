---
layout: post
titile: Unix OS: Chapter2 the introduction to the kernel
date: 2017-05-14
---
文件和进程是Unix系统最核心的两个概念。内核包含了这两个概念的重要部分，分别是`file subsystem`和`process control subsystem`。system call和library间的接口代表了用户程序和内核之间的边界。

# file subsystem
Unix系统内部不使用文件名，而使用inode号码来识别文件。inode存储文件的元信息，也叫`索引节点`。如文件字节数、拥有者ID、读写执行权限、时间戳、链接数、数据block位置等。inode节点数在格式化时就给定了，所以存在inode用光、而硬盘还未占满的情况。

系统内部分三步打开一个文件：
- 系统找到这个文件名对应的inode号码
- 通过inode号码获取inode信息
- 根据inode信息找到文件数据所在的block，读出数据
