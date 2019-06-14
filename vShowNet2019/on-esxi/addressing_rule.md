## ESXi

- vsr
    - 172.16.243.66
    - 10.0.250.196

- vshownet
    - 172.16.243.65
    - 10.0.250.55

## DeviceID
- ホスト名の数字部分．`R100`なら`100`，`PE001`なら`001`

## inter domain p2p link
- 192.0.2.0/24


## WAN
- 198.18.0.0/15
- 198.51.100.0/24

## management
- 172.31.0.0/24

- マネジメントアドレスは．`172.31.0.DeviceID`
- マネジメントには，踏台にsshして入る．
    - vShowNet: 10.0.249.101
    - vSR: 10.0.250.247

## eBGP

- 203.0.113.0/24


```yaml
PE001 -- R100: linkid 900: 203.0.113.0/30
PE002 -- R101: linkid 901: 203.0.113.4/30
PE003 -- R102: linkid 902: 203.0.113.8/30
PE004 -- R103: linkid 903: 203.0.113.12/30

PE001 -- R200: linkid 910: 203.0.113.40/30
PE002 -- R201: linkid 911: 203.0.113.44/30
PE003 -- R202: linkid 912: 203.0.113.48/30
PE004 -- R203: linkid 913: 203.0.113.52/30

p2p-link LinkID(VlanID): 900〜963
p2p-link ipv4: 203.0.113.(LinkID - 900)*4/30
p2p-link ipv6: 2001:db8:113:LinkID::X/128

```

## SR-domain

DeviceIDは `0xx`

```yaml
IPv4 CIDR block: 100.64.0.0/16
IPv6 CIDR block: 2001:db8:64::/48
loop back ipv4: 100.64.0.X/32
loop back ipv6: 2001:db8:64::X/128
p2p-link LinkID(VlanID): 000〜063
p2p-link ipv4: 100.64.1.(LinkID - 0)*4/30
p2p-link ipv6: 2001:db8:64:LinkID::X/128
p2p-link link-local: fe80::LinkID:X/64

SRv6 SID: a:b:c:X::/64

```

## vShowNet-1

DeviceIDは `1xx`

```yaml
IPv4 CIDR block: 100.65.0.0/16
IPv6 CIDR block: 2001:db8:65::/48
loop back ipv4: 100.65.0.X/32
loop back ipv6: 2001:db8:65::X/128
p2p-link LinkID(VlanID): 100〜163
p2p-link ipv4: 100.65.1.(LinkID - 100)*4/30
p2p-link ipv6: 2001:db8:65:LinkID::X/128
p2p-link link-local: fe80::LinkID:X/64
```

## vShowNet-2

DeviceIDは `2xx`

```yaml
IPv4 CIDR block: 100.66.0.0/16
IPv6 CIDR block: 2001:db8:66::/48
loop back ipv4: 100.66.0.X/32
loop back ipv6: 2001:db8:66::X/128
p2p-link LinkID(VlanID): 200〜263
p2p-link ipv4: 100.66.1.(LinkID - 200)*4/30
p2p-link ipv6: 2001:db8:66:LinkID::X/128
p2p-link link-local: fe80::LinkID:X/64
```

