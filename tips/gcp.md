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
```

{% hint style="info" %}
 Super-powers are granted randomly so please submit an issue if you're not happy with yours.
{% endhint %}

Once you're strong enough, save the world:

```
// Ain't no code for that yet, sorry
echo 'You got to trust me on this, I saved the world'
```



