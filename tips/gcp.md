# GCP

## 1、配置主机

配置选择，端口防火墙配置。

## 2、配置SS

```
#管理员权限运行命令
sudo –i
#更新package
apt update
apt upgrade
#内核更新
apt autoremove
update-grub
Reboot
#启用BBR加速
echo "net.core.default_qdisc=fq" >> /etc/sysctl.conf
echo "net.ipv4.tcp_congestion_control=bbr" >> /etc/sysctl.conf
#配置生效
sysctl -p
#检验BBR是否生效
lsmod | grep bbr
#看到回显tcp_bbr 20480 0说明已经成功开启 BBR
#安装SS
sudo apt-get install python-pip
sudo pip install shadowsocks
#新建配置文件
sudo vim /etc/ss-conf.json
#例子
{
"server":"0.0.0.0",
"server_port":对外开放的端口,
"local_address":"127.0.0.1",
"local_port":1080,
"password":"密码",
"timeout":600,
"method":"aes-256-cfb"
}
#以该配置文件启动SS
sudo ssserver -c /etc/ss-conf.json -d start
sudo ssserver -c /etc/ss-conf.json -d restart
```

## 3、设置SS自启动

```text
#创建自启动脚本
sudo vim /etc/init.d/shadowsocks
#内容
#!/bin/sh
### BEGIN INIT INFO
# Provides:          shadowsocks
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: start shadowsocks
# Description:       start shadowsocks
### END INIT INFO
start(){
        ssserver -c /etc/ss-conf.json -d start
}
stop(){
        ssserver -c /etc/ss-conf.json -d stop
}
case "$1" in
start)
        start
        ;;
stop)
        stop
        ;;
reload)
        stop
        start
        ;;
*)
        echo "Usage: $0 {start|reload|stop}"
        exit 1
        ;;
esac
#修改可执行权限
sudo chmod +x /etc/init.d/shadowsocks
#执行
sudo update-rc.d shadowsocks defaults
```

