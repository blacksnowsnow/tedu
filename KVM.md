搭建KVM服务器

virtualization资源管理
	x个物理资源 --> y个逻辑资源
	实现程度：完全、部分、硬件辅助

虚拟化主要厂商及产品

主要软件组
	虚拟化平台—— "Virtualization Platform"
	虚拟化主机——"Virtualization Host"
	虚拟化客户端—— "Virtualzation Client"

2）查看全部软件组，过滤出与虚拟化相关的软件组
[root@mysql51 logs]# yum  group  list hidden |grep -i 虚拟
步骤二：确认RHEL7中的虚拟化软件组
1）安装兼容组信息虚拟化客户端
[root@kvmsvr ~]# yum  -y groups install 虚拟化平台 虚拟化客户端

2）确保libvirtd服务可用
[root@kvmsvr ~]# systemctl  restart  libvirtd
[root@kvmsvr ~]# systemctl  enable  libvirtd


本例要求在真实KVM服务器上完成以下任务：
新建一个名为 rhel7.2 的虚拟机，并为其安装好操作系统（注意禁用SELinux机制、禁用防火墙）
将虚拟机 rhel7.2 克隆为 rhel7-c1
开启虚拟机 rhel7-c1 ，以 root 用户登入到系统
彻底删除虚拟机 rhel7-c1
2.2 方案

使用KVM提供的virt-manager图形化管理程序来操作。
2.3 步骤

实现此案例需要按照如下步骤进行。
步骤一：新建名为rhel7.2的虚拟机
1）在“虚拟系统管理器”中单击左上方“创建新虚拟机”按钮（如图-3所示）。

2）弹出“新建虚拟机”向导，选择“本地安装介质”（如图-4所示），单击“前进”。

3）接下来“定位安装介质”，请正确指定RHEL7系统的ISO光盘镜像文件位置（如图-5所示），确认自动识别到操作系统类型，单击“前进”。





















