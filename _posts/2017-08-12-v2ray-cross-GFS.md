---
layout: post
title: Cross the "wall" using V2ray
author: Author Heming
---

由于众所周知的原因，国内翻墙已经开始出现不稳的迹象。像shadowsocks之类的工具已经开始被干扰，作者们也被请去喝茶。
这个post所用的代理是v2ray,目前还没有被干扰。项目的官方网站是
Link: [V2ray](https://github.com/v2ray/v2ray-core)

## 选择VPS
想要搭建一个私有的翻墙代理，需要有一个自己的server.比较常用的有搬瓦工(bandwagon), digitalocean等等。需要注意的是翻墙的网速跟你vps节点所在的位置有很大的关系，一般来说台湾，日本，新加坡的节点速度较快较稳定。具体的速度因人而异，可以先对不同节点进行测速再进行选择。
## 服务器端
先通过ssh命令登录服务器端，然后运行安装脚本
~~~
wget https://raw.githubusercontent.com/v2ray/v2ray-core/master/release/install-release.sh
~~~
进行安装
~~~
sudo chmod +x install-release.sh
sudo ./install-release.sh && rm ./install-release.sh
~~~
默认路径安装在/usr/bin/v2ray目录下，通过系统的service来启动。
~~~
sudo service v2ray start
~~~
## 服务器参数配置

~~~
{
  "port": 12345, //通讯端口，客户端和服务端一致，自定
  "log" : {
    "access": "/var/log/v2ray/access.log", 
    "error": "/var/log/v2ray/error.log",  
    "loglevel": "warning"                  
  },
  "inbound": {
    "protocol": "vmess",    
    "settings": {
      "clients": [
        {
          "id": "293c95b0-a4a2-47d5-b6eb-da8e6894e7b8",  //UUID 在这个网站随机生成一个，https://www.uuidgenerator.net， 要保证client和server配置一个UUID
          "alterId": 55,  // 这个自定，数字范围0-100，但要保证客户端和服务端一致
          "level": 1  // 官方说明，0 共享VPS, 1 自用VPS
        }
      ]
    }
  },
  "outbound": {
    "protocol": "freedom",  
    "settings": {}
  },
  "inboundDetour": [
    {
      "protocol": "shadowsocks",   // 此段为支持SS协议部分
      "port": 1234, 
      "settings": {
        "method": "chacha20", // 加密协议支持aes-256-cfb, aes-128-cfb, chacha20 (V2Ray 1.9+), chacha20-ietf (V2Ray 1.9+)
        "password": "v2ray",     
        "udp": false             //是否支持UDP中转
      }
    }
  ],
  "outboundDetour": [
    {
      "protocol": "blackhole",  
      "settings": {},
      "tag": "blocked"
    }
  ],
  "routing": {
    "strategy": "rules",
    "settings": {
      "rules": [
        {
          "type": "field",  
          "ip": [
            "0.0.0.0/8",
            "10.0.0.0/8",
            "100.64.0.0/10",
            "127.0.0.0/8",
            "169.254.0.0/16",
            "172.16.0.0/12",
            "192.0.0.0/24",
            "192.0.2.0/24",
            "192.168.0.0/16",
            "198.18.0.0/15",
            "198.51.100.0/24",
            "203.0.113.0/24",
            "::1/128",
            "fc00::/7",
            "fe80::/10"
          ],
          "outboundTag": "blocked"
        }
      ]
    }
  }
}
~~~

## Linux客户端配置
以下针对Ｌｉｎｕｘ用户, 用于上文相同的方式安装v2ray，然后修改配置文件(/etc/v2ray/config.json)。

要确保服务器ip,port, userid, alterid与服务器配置一致。

修改成功后，写一个启动脚本
~~~
vi v2ray_init.sh

~~~
~~~
sudo /usr/bin/v2ray/v2ray --config /etc/v2ray/config.json
~~~
增加执行权限,执行
~~~
chmod +x ./v2ray_init.sh
./v2ray_init.sh
~~~

为chrome设置socket5代理，设为 127.0.0.1:1080 (或者设置全局代理)，就可以翻墙了。

如果想要让脚本开机执行的话，将命令添加到/etc/rc.local

## 其他系统的客户端
V2ray支持Windows, IOS, Android, Mac　并有专门的第三方客户端，具体信息请参见
[link](https://www.v2ray.com/chapter_01/3rd_party.html)