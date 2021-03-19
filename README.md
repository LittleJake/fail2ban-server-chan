# fail2ban-server-chan
Fail2Ban连结server酱进行IP封禁提醒

## 使用方式

下载配置文件至fail2ban的action.d目录
```shell
cd /etc/fail2ban/action.d
sudo wget https://cdn.jsdelivr.net/gh/LittleJake/fail2ban-server-chan/server-chan.conf
```

编辑server-chan.conf，将sckey行修改为你的server酱SCKEY。
```conf
# Option:  server_chan_sckey
# Notes    Your sckey from sc.ftqq.com
# Values:  STRING  Default: None
# Register for abuseipdb [https://sc.ftqq.com/], get sckey and set below.
server_chan_sckey = 你的SCKEY
```

同时，在/etc/fail2ban/jail.local添加对应规则内action
```conf
# 单行action
action = server-chan

# 多个action
action = iptables[name=SSH, port=22, protocol=tcp]
         server-chan
```

最后，重新读取配置即可。
```shell
systemctl reload fail2ban
```

### 效果
![demo](https://cdn.jsdelivr.net/gh/LittleJake/blog-static-files@imgs/imgs/20210319162716.jpg)

### 开源协议
Apache 2.0
