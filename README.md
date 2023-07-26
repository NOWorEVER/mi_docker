#小米万兆路由器 docker 安装Aria2下载器，流程版
-------------------------------------------------------
​​网上的教程五花八门，基本都是一些【大佬】三言两语就讲完一套复杂的东西

作为一个半吊子，也是花了大半天时间才搞清楚。

所以这篇文章会以一个纯小白的流程来将这个流程讲清楚

该教程理论上也支持其他支持小米docker的路由器

-------------------------------------------------------
所需工具：
---
Windows【连接硬盘进行格式化】

DiskGenius【将硬盘格式化为EXT4】自行获取

代码以及其他文件请到Releases中获取

小米万兆路由器

硬(磁)盘【不推荐U盘】U盘大小也要超过32GB，最小需要选择64GB的U盘。

-------------------------------------------------------
第一步：外接磁盘安装Docker
---

(因为本次安装的是下载器，所以一般的U盘可能扛不住，所以尽量选择硬盘)

硬盘需要先格式化为【EXT4】格式，推荐工具为【DiskGenius】免费版本就能用

右键选择需要格式的盘，【注意不要格式错盘】【注意不要格式错盘】【注意不要格式错盘】

选择【格式化当前分区】，之后选择文件系统为【EXT4】,点击【格式化】后完成操作。
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/ece9acfe-dbbf-4e4a-8d06-d405d4179f90)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/5f06e836-6b8c-4cee-9bcb-ea8719dde831)



完成后断开磁盘，用DiskGenius【安全弹出磁盘】

​将磁盘连接安装到万兆路由器
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/d07f9c8b-824a-4e3e-b0ab-a2688bac2b19)

打开小米路由器管理地址，默认为【 192.168.31.1 】进行登录
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/7c6abce9-3d8b-46cb-b9f2-696c291f22bf)
登录后进入【存储功能】，查看磁盘是否成功连接，建议打开USB3.0(不打开也行，看你能不能忍)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/5fc9c833-53bd-47d1-818a-c248e9e68ba7)
有看到磁盘后则可以点击【Docker】进行安装运行

安装流程：点击【Docker】→【安装第三方管理】→【管理Docker】

默认账号密码都为admin

![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/01b9cb40-e15b-43ae-a90d-38929aef7c4b)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/d75267d5-ff11-40d5-b532-0fcc05cf80a2)

第二步：镜像安装
---
登录后选择【镜像管理】→选择【拉取】

输入【nginx:alpine-slim】点击【OK】等待安装完成（之前安装过就不用再安装了）
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/101b2a58-c9c4-4a06-88e3-9d36d88aceaa)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/324311c2-24af-446a-aa9f-79c40af70224)
获取挂载路径
​复制【挂载点(MountPoint)】的内容，找个记事本写进去
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/11d796cd-245a-439e-9a65-b5a48a2716e7)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/6a34bc28-723b-4b60-93f6-9541e822cdb8)
完成后回到镜像管理，检查镜像管理，确认无误后点击运行，选择【专业模式】

(其他两个镜像完成全部流程后就会安装成功)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/ea042e6a-5ed8-4c13-a46c-7d55bf8dc625)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/46e53f6e-79d7-49a7-9014-1659450dabc4)

专业模式中的挂载路径与Simple-Docker一致。可以重新开一个窗口进行对照复制
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/2399d1bc-bfb3-4389-8edc-58f6c19c812e)
​每个人从存储配置不一致，看自己的就行
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/8cddee38-8e08-4245-8926-e3a756ecffe2)
​容器名称自己可以随便取，我这边名字是【nginx】，下一步后点击【新增挂载】
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/2f5b61c7-68be-45f6-8cdb-8aeab5079b6d)
​需要挂载两个目录
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/87ac691c-323f-4de0-ac3b-30f4fa9426d5)
网络选择【bridge】，然后一直下一步
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/eb23bb87-5866-4871-b2af-6235932f493e)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/6e71cdd7-9405-4ad8-8d30-6c8fbde78a47)

如果有错误提示请看下方
---
如果你弹出创建的错误。不是你操作有问题，而是新版本小米直接把权限没收了

如果你之前没有开通过ssh或者没有进行固化操作

则需要通过小米路由器官网下载路由器修复工具进行降级,该文件已经存放在https://github.com/NOWorEVER/mi_docker/releases 中

官方链接：http://www1.miwifi.com/miwifi_download.html

固件包链接：https://cdn.cnbj1.fds.api.mi-img.com/xiaoqiang/rom/rc01/miwifi_rc01_firmware_7d764_1.0.53.bin


该链接由@酱紫表 ​提供，ssh的教程在大佬博客中 https://blog.qust.me/be10000

如果你之前固化了ssh，则可以在ssh中使用这段命令行来恢复权限

sed -i "s/authorization_plugins.*/authorization_plugins ''/g" /etc/config/mi_docker

小插曲结束！

---------------------------------------
接着回到【容器管理】，检查【名称】和【镜像】后点击开关旁边的【终端】（方块）
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/243b8e72-7fbd-48ba-8b95-73cd50fa39c2)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/785d3d6e-be55-473c-8ea6-f17c221cb8e5)

代码部分
---
所需代码都已经上传到 https://github.com/NOWorEVER/mi_docker/releases/


安装docker-cli第一步先更换阿里源(直连不稳定)

########代码部分########

# 更换阿里云源

sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

 

# 更新阿里云源

apk update

 

# 安装docker-cli

apk add docker-cli

########代码部分########

​完成上方三段代码后要进行文本替换了

【先将下列代码复制到记事本中】文章顶部有文本分享文件，如果文字错乱请用记事本文件

 

docker run -d \ 
--name aria2-pro \

--restart unless-stopped \

--log-opt max-size=1m \

-e PUID=$UID \

-e PGID=$GID \

-e UMASK_SET=022 \

-e RPC_SECRET=<TOKEN> \

-e RPC_PORT=6800 \

-p 6800:6800 \

-e LISTEN_PORT=6888 \

-p 6888:6888 \

-p 6888:6888/udp \

-v <CONFIG>:/config \

-v <DOWNLOADS>:/downloads \

p3terx/aria2-pro

​

​【完成后进行替换<TOKEN>，<CONFIG>，<DOWNLOADS>，替换最终结果没有<>符号】

​<TOKEN>：这个是用户自行设置的密码【123456】【admin】都行

​<CONFIG>：是上方的【挂载路径】，每个人都不一样

​(我的是/mnt/usb-973c0b10/mi_docker/lib/docker/volumes/8777fecfab9f099a73fd8267a61862a758a426c6dd3cc039dd0e56181098a6b0/_data)

​<DOWNLOADS>：/mnt/usb-*******/downloads，和前面一样查看【挂载路径】，记得查看硬盘中有没有【downloads】这个文件夹，没有的话自己新建一个在磁盘中
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/6e59e3e7-3ab8-4dda-b266-f187e4090307)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/ee3dea97-bf1a-4742-a9e5-816929b9c2c1)
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/27ca8556-df1d-4131-902d-5047966e4a29)
【完成替换后又可以开始粘贴代码了】
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/0d4dcf4b-3663-4593-aa3b-304b0e0c4dd1)
将代码粘贴后回车。下载器就安装完成了。但是下载器的图形控制器还没有安装完成
安装 AriaNg 图形管理器

​无脑粘贴代码回车即可

#########代码部分##########

docker run -d \     
--name ariang \     
--log-opt max-size=1m \     
--restart unless-stopped \     
-p 6880:6880 \     
p3terx/ariang

#########代码部分##########

 

完成后浏览器进入【http://192.168.31.1:6880 】(路由器ip:6880)每个人可能不一样，但是后面的:6880是一样的
​![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/e10ff109-1957-44fd-aae9-2fc74c14b12f)
进入后将密钥输入，输入后右上角会弹窗，点击【重新加载AriaNg】即可

密钥为前面输入的​<TOKEN>

![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/4b3f51b4-ccf4-4127-b8fe-033342b46044)
重启后点击【新建】输入链接就可以了【这个不用我教了吧】
![image](https://github.com/NOWorEVER/mi_docker/assets/57054154/9e7d7032-d652-443b-b4e3-dd3c735a6822)
完成！！！！

​按照我这个流程应该半小时就能搞定，但是网上的教程都是含糊两句就带过，对小白太不友好了。

​还有啥问题请留言，看看能不能帮忙解决


