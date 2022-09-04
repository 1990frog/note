<!-- TOC -->

- [安装](#安装)
- [规则](#规则)
- [mode](#mode)
- [fake-ip](#fake-ip)
- [script](#script)
- [config](#config)
- [systemd服务](#systemd服务)

<!-- /TOC -->

# 安装
linux（archlinuxcn/clash-premium-bin）

# 规则
DOMAIN-SUFFIX：域名后缀匹配
DOMAIN：域名匹配
DOMAIN-KEYWORD：域名关键字匹配
IP-CIDR：IP段匹配
SRC-IP-CIDR：源IP段匹配
GEOIP：GEOIP数据库（国家代码）匹配
DST-PORT：目标端口匹配
SRC-PORT：源端口匹配
MATCH：全匹配（一般放在最后）

# mode
https://lancellc.gitbook.io/clash/

tproxy
tap
tun

# fake-ip

# script
```
script:
  code: |
    def main(ctx, metadata):
      ip = ctx.resolve_ip(metadata["host"])
      if ip == "":
        return "DIRECT"
        
      code = ctx.geoip(ip)
      if code == "LAN" or code == "CN":
        return "DIRECT"
      
      return "Proxy" # default policy for requests which are not matched by any other script
```

# config
```yaml
#tun:
#  enable: true
#  stack: system # or gvisor
#  # dns-hijack:
#  #   - 8.8.8.8:53
#  #   - tcp://8.8.8.8:53
#  auto-route: true # auto set global route
#  auto-detect-interface: true # conflict with interface-name

# http端口
#port: 7890

# socks5端口
#socks-port: 7891

# Linux 和 macOS 的 redir 代理端口 (如需使用此功能，请取消注释)
#redir-port: 7892

# 混合端口
mixed-port: 7890

# 规则模式：Rule（规则） / Global（全局代理）/ Direct（全局直连）
mode: rule

# 设置日志输出级别 (默认级别：silent，即不输出任何内容，以避免因日志内容过大而导致程序内存溢出）。
# 5 个级别：silent / info / warning / error / debug。级别越高日志输出量越大，越倾向于调试，若需要请自行开启
log-level: silent

# 局域网访问
allow-lan: true

# clash 的 RESTful API
external-controller: 0.0.0.0:9090
secret: '123456'
bind-address: "*"

# ui地址
#external-ui: "/usr/share/openclash/dashboard"

# 1. clash DNS 请求逻辑：
#   (1) 当访问一个域名时， nameserver 与 fallback 列表内的所有服务器并发请求，得到域名对应的 IP 地址。
#   (2) clash 将选取 nameserver 列表内，解析最快的结果。
#   (3) 若解析结果中，IP 地址属于 国外，那么 clash 将选择 fallback 列表内，解析最快的结果。
#
#   因此，我在 nameserver 和 fallback 内都放置了无污染、解析速度较快的国内 DNS 服务器，以达到最快的解析速度。
#   但是 fallback 列表内服务器会用在解析境外网站，为了结果绝对无污染，我仅保留了支持 DoT/DoH 的两个服务器。
# 
# 2. clash DNS 配置注意事项：
#   (1) 如果您为了确保 DNS 解析结果无污染，请仅保留列表内以 tls:// 或 https:// 开头的 DNS 服务器，但是通常对于国内域名没有必要。
#   (2) 如果您不在乎可能解析到污染的结果，更加追求速度。请将 nameserver 列表的服务器插入至 fallback 列表内，并移除重复项。
# 
# 3. 关于 DNS over HTTPS (DoH) 和 DNS over TLS (DoT) 的选择：
#   对于两项技术双方各执一词，而且会无休止的争论，各有利弊。各位请根据具体需求自行选择，但是配置文件内默认启用 DoT，因为目前国内没有封锁或管制。
#   DoH: 以 https:// 开头的 DNS 服务器。拥有更好的伪装性，且几乎不可能被运营商或网络管理封锁，但查询效率和安全性可能略低。
#   DoT: 以 tls:// 开头的 DNS 服务器。拥有更高的安全性和查询效率，但端口有可能被管制或封锁。
#   若要了解更多关于 DoH/DoT 相关技术，请自行查阅规范文档。
dns:
  enable: true
  ipv6: false
  # enhanced-mode: redir-host # 或 fake-ip
  enhanced-mode: fake-ip
  fake-ip-range: 198.18.0.1/16
  listen: 127.0.0.1:7874
  # fake-ip-filter: # fake-ip 白名单列表
  fake-ip-filter:
  - "*.lan"
  - time.windows.com
  - time.nist.gov
  - time.apple.com
  - time.asia.apple.com
  - "*.ntp.org.cn"
  - "*.openwrt.pool.ntp.org"
  - time1.cloud.tencent.com
  - time.ustc.edu.cn
  - pool.ntp.org
  - ntp.ubuntu.com
  - ntp.aliyun.com
  - ntp1.aliyun.com
  - ntp2.aliyun.com
  - ntp3.aliyun.com
  - ntp4.aliyun.com
  - ntp5.aliyun.com
  - ntp6.aliyun.com
  - ntp7.aliyun.com
  - time1.aliyun.com
  - time2.aliyun.com
  - time3.aliyun.com
  - time4.aliyun.com
  - time5.aliyun.com
  - time6.aliyun.com
  - time7.aliyun.com
  - "*.time.edu.cn"
  - time1.apple.com
  - time2.apple.com
  - time3.apple.com
  - time4.apple.com
  - time5.apple.com
  - time6.apple.com
  - time7.apple.com
  - time1.google.com
  - time2.google.com
  - time3.google.com
  - time4.google.com
  - music.163.com
  - "*.music.163.com"
  - "*.126.net"
  - musicapi.taihe.com
  - music.taihe.com
  - songsearch.kugou.com
  - trackercdn.kugou.com
  - "*.kuwo.cn"
  - api-jooxtt.sanook.com
  - api.joox.com
  - joox.com
  - y.qq.com
  - "*.y.qq.com"
  - streamoc.music.tc.qq.com
  - mobileoc.music.tc.qq.com
  - isure.stream.qqmusic.qq.com
  - dl.stream.qqmusic.qq.com
  - aqqmusic.tc.qq.com
  - amobile.music.tc.qq.com
  - "*.xiami.com"
  - "*.music.migu.cn"
  - music.migu.cn
  - "*.msftconnecttest.com"
  - "*.msftncsi.com"
  - localhost.ptlogin2.qq.com
  - "+.srv.nintendo.net"
  - "+.stun.playstation.net"
  - xbox.*.microsoft.com
  - "+.xboxlive.com"
  - proxy.golang.org
  - stun.*.*
  - stun.*.*.*
  - heartbeat.belkin.com
  - "*.linksys.com"
  - "*.linksyssmartwifi.com"
  - "+.battlenet.com.cn"
  nameserver:
  - 114.114.114.114
  - 119.29.29.29
  # 与 nameserver 内的服务器列表同时发起请求，当规则符合 GEOIP 在 CN 以外时，fallback 列表内的域名服务器生效
  fallback:
  - https://cloudflare-dns.com/dns-query
  - https://dns.google/dns-query
  - https://1.1.1.1/dns-query
  - tls://8.8.8.8:853
  fallback-filter:
    geoip: false
    # 在这个网段内的 IP 地址会被考虑为被污染的 IP
    ipcidr:
    - 0.0.0.0/8
    - 10.0.0.0/8
    - 100.64.0.0/10
    - 127.0.0.0/8
    - 169.254.0.0/16
    - 172.16.0.0/12
    - 192.0.0.0/24
    - 192.0.2.0/24
    - 192.88.99.0/24
    - 192.168.0.0/16
    - 198.18.0.0/15
    - 198.51.100.0/24
    - 203.0.113.0/24
    - 224.0.0.0/4
    - 240.0.0.0/4
    - 255.255.255.255/32
    domain:
    - "+.google.com"
    - "+.facebook.com"
    - "+.youtube.com"
    - "+.githubusercontent.com"
ipv6: false

proxies:
- name: "vmess"
  type: vmess
  server: xxxx
  port: xxxx
  uuid: xxxx
  alterId: xxxxx
  cipher: auto
proxy-groups:
- name: Auto - UrlTest
  type: url-test
  proxies:
  - "vmess"
  url: https://cp.cloudflare.com/generate_204
  interval: '600'
  tolerance: '150'
- name: Proxy
  type: select
  proxies:
  - Auto - UrlTest
  - DIRECT
- name: Domestic
  type: select
  proxies:
  - DIRECT
  - Proxy
- name: Others
  type: select
  proxies:
  - Proxy
  - DIRECT
  - Domestic
- name: Microsoft
  type: select
  proxies:
  - DIRECT
  - Proxy
- name: Apple
  type: select
  proxies:
  - DIRECT
  - Proxy
- name: Scholar
  type: select
  proxies:
  - Proxy
  - DIRECT
- name: Netflix
  type: select
  proxies:
  - GlobalTV
  - DIRECT
- name: Disney
  type: select
  proxies:
  - GlobalTV
  - DIRECT
- name: Youtube
  type: select
  disable-udp: true
  proxies:
  - GlobalTV
  - DIRECT
- name: Spotify
  type: select
  proxies:
  - GlobalTV
  - DIRECT
- name: Steam
  type: select
  proxies:
  - DIRECT
  - Proxy
- name: AdBlock
  type: select
  proxies:
  - REJECT
  - DIRECT
  - Proxy
- name: AsianTV
  type: select
  proxies:
  - DIRECT
  - Proxy
- name: GlobalTV
  type: select
  proxies:
  - Proxy
  - DIRECT
- name: Speedtest
  type: select
  proxies:
  - Proxy
  - DIRECT
- name: Telegram
  type: select
  proxies:
  - Proxy
  - DIRECT
- name: PayPal
  type: select
  proxies:
  - DIRECT
  - Proxy
rules:
- RULE-SET,Reject,AdBlock
- RULE-SET,Special,DIRECT
- RULE-SET,Netflix,Netflix
- RULE-SET,Spotify,Spotify
- RULE-SET,YouTube,Youtube
- RULE-SET,Disney Plus,Disney
- RULE-SET,Bilibili,AsianTV
- RULE-SET,iQiyi,AsianTV
- RULE-SET,Letv,AsianTV
- RULE-SET,Netease Music,AsianTV
- RULE-SET,Tencent Video,AsianTV
- RULE-SET,Youku,AsianTV
- RULE-SET,WeTV,AsianTV
- RULE-SET,ABC,GlobalTV
- RULE-SET,Abema TV,GlobalTV
- RULE-SET,Amazon,GlobalTV
- RULE-SET,Apple News,GlobalTV
- RULE-SET,Apple TV,GlobalTV
- RULE-SET,Bahamut,GlobalTV
- RULE-SET,BBC iPlayer,GlobalTV
- RULE-SET,DAZN,GlobalTV
- RULE-SET,Discovery Plus,GlobalTV
- RULE-SET,encoreTVB,GlobalTV
- RULE-SET,Fox Now,GlobalTV
- RULE-SET,Fox+,GlobalTV
- RULE-SET,HBO,GlobalTV
- RULE-SET,Hulu Japan,GlobalTV
- RULE-SET,Hulu,GlobalTV
- RULE-SET,Japonx,GlobalTV
- RULE-SET,JOOX,GlobalTV
- RULE-SET,KKBOX,GlobalTV
- RULE-SET,KKTV,GlobalTV
- RULE-SET,Line TV,GlobalTV
- RULE-SET,myTV SUPER,GlobalTV
- RULE-SET,Pandora,GlobalTV
- RULE-SET,PBS,GlobalTV
- RULE-SET,Pornhub,GlobalTV
- RULE-SET,Soundcloud,GlobalTV
- RULE-SET,ViuTV,GlobalTV
- RULE-SET,Telegram,Telegram
- RULE-SET,Steam,Steam
- RULE-SET,Speedtest,Speedtest
- RULE-SET,PayPal,PayPal
- RULE-SET,Microsoft,Microsoft
- RULE-SET,PROXY,Proxy
- RULE-SET,Apple,Apple
- RULE-SET,Scholar,Scholar
- RULE-SET,Domestic,Domestic
- RULE-SET,Domestic IPs,Domestic
- RULE-SET,LAN,DIRECT
- IP-CIDR,198.18.0.1/16,REJECT,no-resolve
- GEOIP,CN,Domestic
- MATCH,Others

profile:
  store-selected: true
rule-providers:
  Reject:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Reject.yaml
    path: "./rule_provider/Reject"
    interval: 86400
  Special:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Special.yaml
    path: "./rule_provider/Special"
    interval: 86400
  Netflix:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Netflix.yaml
    path: "./rule_provider/Netflix"
    interval: 86400
  Spotify:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Spotify.yaml
    path: "./rule_provider/Spotify"
    interval: 86400
  YouTube:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/YouTube.yaml
    path: "./rule_provider/YouTube"
    interval: 86400
  Bilibili:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Bilibili.yaml
    path: "./rule_provider/Bilibili"
    interval: 86400
  iQiyi:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/iQiyi.yaml
    path: "./rule_provider/iQiyi"
    interval: 86400
  Letv:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Letv.yaml
    path: "./rule_provider/Letv"
    interval: 86400
  Netease Music:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Netease%20Music.yaml
    path: "./rule_provider/Netease_Music"
    interval: 86400
  Tencent Video:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Tencent%20Video.yaml
    path: "./rule_provider/Tencent_Video"
    interval: 86400
  Youku:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Youku.yaml
    path: "./rule_provider/Youku"
    interval: 86400
  WeTV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/WeTV.yaml
    path: "./rule_provider/WeTV"
    interval: 86400
  ABC:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/ABC.yaml
    path: "./rule_provider/ABC"
    interval: 86400
  Abema TV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Abema%20TV.yaml
    path: "./rule_provider/Abema_TV"
    interval: 86400
  Amazon:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Amazon.yaml
    path: "./rule_provider/Amazon"
    interval: 86400
  Apple News:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Apple%20News.yaml
    path: "./rule_provider/Apple_News"
    interval: 86400
  Apple TV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Apple%20TV.yaml
    path: "./rule_provider/Apple_TV"
    interval: 86400
  Bahamut:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Bahamut.yaml
    path: "./rule_provider/Bahamut"
    interval: 86400
  BBC iPlayer:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/BBC%20iPlayer.yaml
    path: "./rule_provider/BBC_iPlayer"
    interval: 86400
  DAZN:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/DAZN.yaml
    path: "./rule_provider/DAZN"
    interval: 86400
  Discovery Plus:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Discovery%20Plus.yaml
    path: "./rule_provider/Discovery_Plus"
    interval: 86400
  Disney Plus:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Disney%20Plus.yaml
    path: "./rule_provider/Disney_Plus"
    interval: 86400
  encoreTVB:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/encoreTVB.yaml
    path: "./rule_provider/encoreTVB"
    interval: 86400
  Fox Now:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Fox%20Now.yaml
    path: "./rule_provider/Fox_Now"
    interval: 86400
  Fox+:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Fox%2B.yaml
    path: "./rule_provider/Fox+"
    interval: 86400
  HBO:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/HBO.yaml
    path: "./rule_provider/HBO"
    interval: 86400
  Hulu Japan:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Hulu%20Japan.yaml
    path: "./rule_provider/Hulu_Japan"
    interval: 86400
  Hulu:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Hulu.yaml
    path: "./rule_provider/Hulu"
    interval: 86400
  Japonx:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Japonx.yaml
    path: "./rule_provider/Japonx"
    interval: 86400
  JOOX:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/JOOX.yaml
    path: "./rule_provider/JOOX"
    interval: 86400
  KKBOX:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/KKBOX.yaml
    path: "./rule_provider/KKBOX"
    interval: 86400
  KKTV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/KKTV.yaml
    path: "./rule_provider/KKTV"
    interval: 86400
  Line TV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Line%20TV.yaml
    path: "./rule_provider/Line_TV"
    interval: 86400
  myTV SUPER:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/myTV%20SUPER.yaml
    path: "./rule_provider/myTV_SUPER"
    interval: 86400
  Pandora:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Pandora.yaml
    path: "./rule_provider/Pandora"
    interval: 86400
  PBS:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/PBS.yaml
    path: "./rule_provider/PBS"
    interval: 86400
  Pornhub:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Pornhub.yaml
    path: "./rule_provider/Pornhub"
    interval: 86400
  Soundcloud:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/Soundcloud.yaml
    path: "./rule_provider/Soundcloud"
    interval: 86400
  ViuTV:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Media/ViuTV.yaml
    path: "./rule_provider/ViuTV"
    interval: 86400
  Telegram:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Telegram.yaml
    path: "./rule_provider/Telegram"
    interval: 86400
  Steam:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Steam.yaml
    path: "./rule_provider/Steam"
    interval: 86400
  Speedtest:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Speedtest.yaml
    path: "./rule_provider/Speedtest"
    interval: 86400
  PayPal:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/PayPal.yaml
    path: "./rule_provider/PayPal"
    interval: 86400
  Microsoft:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Microsoft.yaml
    path: "./rule_provider/Microsoft"
    interval: 86400
  PROXY:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Proxy.yaml
    path: "./rule_provider/Proxy"
    interval: 86400
  Domestic:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Domestic.yaml
    path: "./rule_provider/Domestic"
    interval: 86400
  Apple:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Apple.yaml
    path: "./rule_provider/Apple"
    interval: 86400
  Scholar:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Scholar.yaml
    path: "./rule_provider/Scholar"
    interval: 86400
  Domestic IPs:
    type: http
    behavior: ipcidr
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/Domestic%20IPs.yaml
    path: "./rule_provider/Domestic_IPs"
    interval: 86400
  LAN:
    type: http
    behavior: classical
    url: https://cdn.jsdelivr.net/gh/lhie1/Rules@master/Clash/Provider/LAN.yaml
    path: "./rule_provider/LAN"
    interval: 86400
script:
  code: |
    def main(ctx, metadata):
        port_list = [21, 22, 23, 53, 80, 123, 143, 194, 443, 465, 587, 853, 993, 995, 998, 2052, 2053, 2082, 2083, 2086, 2095, 2096, 5222, 5228, 5229, 5230, 8080, 8443, 8880, 8888, 8889]
        ruleset_action = {"Reject": "AdBlock",
            "Special": "DIRECT",
            "Netflix": "Netflix",
            "Spotify": "Spotify",
            "YouTube": "Youtube",
            "Disney Plus": "Disney",
            "Bilibili": "AsianTV",
            "iQiyi": "AsianTV",
            "Letv": "AsianTV",
            "Netease Music": "AsianTV",
            "Tencent Video": "AsianTV",
            "Youku": "AsianTV",
            "WeTV": "AsianTV",
            "ABC": "GlobalTV",
            "Abema TV": "GlobalTV",
            "Amazon": "GlobalTV",
            "Apple News": "GlobalTV",
            "Apple TV": "GlobalTV",
            "Bahamut": "GlobalTV",
            "BBC iPlayer": "GlobalTV",
            "DAZN": "GlobalTV",
            "Discovery Plus": "GlobalTV",
            "encoreTVB": "GlobalTV",
            "Fox Now": "GlobalTV",
            "Fox+": "GlobalTV",
            "HBO": "GlobalTV",
            "Hulu Japan": "GlobalTV",
            "Hulu": "GlobalTV",
            "Japonx": "GlobalTV",
            "JOOX": "GlobalTV",
            "KKBOX": "GlobalTV",
            "KKTV": "GlobalTV",
            "Line TV": "GlobalTV",
            "myTV SUPER": "GlobalTV",
            "Pandora": "GlobalTV",
            "PBS": "GlobalTV",
            "Pornhub": "GlobalTV",
            "Soundcloud": "GlobalTV",
            "ViuTV": "GlobalTV",
            "Telegram": "Telegram",
            "Steam": "Steam",
            "Speedtest": "Speedtest",
            "PayPal": "PayPal",
            "Microsoft": "Microsoft",
            "PROXY": "Proxy",
            "Apple": "Apple",
            "Scholar": "Scholar",
            "Domestic": "Domestic",
            "Domestic IPs": "Domestic",
            "LAN": "DIRECT"
            }
        port = int(metadata["dst_port"])

        if port not in port_list:
            return "DIRECT"

        for rule_name in ctx.rule_providers.keys():
            if ctx.rule_providers[rule_name].match(metadata):
                return ruleset_action[rule_name]

        ip = metadata["dst_ip"] or ctx.resolve_ip(metadata["host"])

        if ip == "":
          return "DIRECT"

        code = ctx.geoip(ip)

        if code == "CN":
          return "Domestic"

        return "Others"
```

# systemd服务
```
> sudo vim /lib/systemd/system/clash@.service

[Unit]
Description=A rule based proxy in Go for %i.
After=network.target

[Service]
Type=simple
User=%i
Restart=on-abort
ExecStart=/usr/bin/clash

[Install]
WantedBy=multi-user.target
```