## 订阅地址转换

https://proxy.fish2018.us.kg/  

## 功能
- 将`hysteria2://`、`trojan://`、`ss://`、`vless://`、`vmess://`协议链接转换为clash可用的代理节点配置
- 支持从`input`目录下的所有txt文档中按行读取代理链接(每条代理链接占一行)
- 支持从`input`目录下的所有yaml/yml读取proxies  
- 支持指定代理类型过滤，指定参数allowed_types=['ss']
- 支持从订阅源提取代理节点，支持订阅源类型:clash、v2ray、trojan、vmess、vless、ss源(链接需以"|ss"结尾)
- 支持从某些github的README.md获取代理节点
- 链接以"|links"结尾，表示链接返回内容中直接包含代理链接，用正则匹配出来
- 支持占位符匹配，Y年m月d日H时M分 例:{Ymd} {Y_m_d} {Y-m-d}
- 支持github文件名模糊匹配，{x}.yaml表示不确定文件名的yaml文件
- 将所有获取的代理节点汇聚到一个配置文件里，自动去重，name重复自动添加随机后缀，分组`自动选择`、`故障转移`、`手动选择`，策略中排除了国内节点    
- 支持全自动批量检测节点有效性，移除失效节点，并按延迟大小排序，无需人工介入（首次执行会自动下载mihomo最新release），自动移除异常节点，修复配置文件
- 可以仅执行批量检测(配置文件名为同目录的clash_config.yaml)
- 支持设置保留节点数，默认保留100个延迟最小的节点
- 生成临时json配置，极大的提高了修复配置异常节点的效率，使用json格式处理几十万行的数据也非常快

## 节点采集源

随便挑几个跑即可，因为通常只会使用比较快的前几个节点，多了也没用，节制才能长久

```
links = [
  "https://gitdl.cn/https://raw.githubusercontent.com/firefoxmmx2/v2rayshare_subcription/main/subscription/clash_sub.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Roywaller/clash_subscription/refs/heads/main/clash_subscription.txt",
  "https://gitdl.cn/https://raw.githubusercontent.com/Q3dlaXpoaQ/V2rayN_Clash_Node_Getter/refs/heads/main/APIs/sc0.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Q3dlaXpoaQ/V2rayN_Clash_Node_Getter/refs/heads/main/APIs/sc1.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Q3dlaXpoaQ/V2rayN_Clash_Node_Getter/refs/heads/main/APIs/sc2.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Q3dlaXpoaQ/V2rayN_Clash_Node_Getter/refs/heads/main/APIs/sc3.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Q3dlaXpoaQ/V2rayN_Clash_Node_Getter/refs/heads/main/APIs/sc4.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/xiaoer8867785/jddy5/refs/heads/main/data/{Y_m_d}/{x}.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/mahdibland/ShadowsocksAggregator/master/LogInfo.txt|links",
  "https://gitdl.cn/https://raw.githubusercontent.com/tglaoshiji/nodeshare/refs/heads/main/{Y}/{m}/{Ymd}.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/mahdibland/SSAggregator/master/sub/sub_merge_yaml.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/mahdibland/ShadowsocksAggregator/master/Eternity.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/vxiaov/free_proxies/main/clash/clash.provider.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/wangyingbo/yb_clashgithub_sub/main/clash_sub.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/ljlfct01/ljlfct01.github.io/refs/heads/main/节点",
  "https://gitdl.cn/https://raw.githubusercontent.com/snakem982/proxypool/main/source/clash-meta.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/leetomlee123/freenode/refs/heads/main/README.md",
  "https://gitdl.cn/https://raw.githubusercontent.com/chengaopan/AutoMergePublicNodes/master/list.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/ermaozi/get_subscribe/main/subscribe/clash.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/zhangkaiitugithub/passcro/main/speednodes.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/skka3134/test/refs/heads/main/clash.yaml|links",
  "https://gitdl.cn/https://raw.githubusercontent.com/mgit0001/test_clash/refs/heads/main/heima.txt",
  "https://gitdl.cn/https://raw.githubusercontent.com/mai19950/clashgithub_com/refs/heads/main/site",
  "https://gitdl.cn/https://raw.githubusercontent.com/aiboboxx/v2rayfree/refs/heads/main/README.md",
  "https://gitdl.cn/https://raw.githubusercontent.com/Pawdroid/Free-servers/refs/heads/main/sub",
  "https://gitdl.cn/https://raw.githubusercontent.com/shahidbhutta/Clash/refs/heads/main/Router",
  "https://gitdl.cn/https://raw.githubusercontent.com/peasoft/NoMoreWalls/master/list.meta.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/skka3134/test/refs/heads/main/test.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/anaer/Sub/refs/heads/main/clash.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/a2470982985/getNode/main/clash.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/free18/v2ray/refs/heads/main/c.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/peasoft/NoMoreWalls/master/list.yml",
  "https://gitdl.cn/https://raw.githubusercontent.com/mfbpn/tg_mfbpn_sub/main/trial.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/Ruk1ng001/freeSub/main/clash.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/ripaojiedian/freenode/main/clash",
  "https://gitdl.cn/https://raw.githubusercontent.com/go4sharing/sub/main/sub.yaml",
  "https://gitdl.cn/https://raw.githubusercontent.com/mfuu/v2ray/master/clash.yaml",
  "https://api.mxlweb.xyz/sub?target=clash&url=https://www.xrayvip.com/free.yaml&insert=false",
  "https://api.mxlweb.xyz/sub?target=clash&url=https://mxlsub.me/free&insert=false",
  "https://www.freeclashnode.com/uploads/{Y}/{m}/0-{Ymd}.yaml",
  "https://www.freeclashnode.com/uploads/{Y}/{m}/1-{Ymd}.yaml",
  "https://clashgithub.com/wp-content/uploads/rss/{Ymd}.yml",
  "https://sub.reajason.eu.org/clash.yaml",
  "https://clash.221207.xyz/pubclashyaml",
  "https://clash.llleman.com/clach.yml",
  "https://proxypool.link/trojan/sub",
  "https://proxypool.link/ss/sub|ss",
  "https://proxypool.link/vmess/sub",
  "https://mxlsub.me/newfull",
  "https://igdux.top/5Hna",
]
```

相关参考：
- https://wiki.metacubex.one/config/  
- https://github.com/Loyalsoldier/geoip  
- https://github.com/MetaCubeX/mihomo/releases  
