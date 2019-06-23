![](topo.jpg)

## RPFについて
送信元アドレスに対する経路を学習していない場合にパケットを破棄する機能．  
VRFを乗り換える場合は，次ホップのルータの受信I/FでRPFが発動するので，予め無効化しておく必要がある．  
各ルータで最低限必要な設定はそれぞれ以下2行．

### R1
```
sysctl -w 'net.ipv4.conf.net0.rp_filter=0'
sysctl -w 'net.ipv4.conf.net0/100.rp_filter=0'
```

### R2
```
sysctl -w 'net.ipv4.conf.net0.rp_filter=0'
sysctl -w 'net.ipv4.conf.net0/200.rp_filter=0'
```
