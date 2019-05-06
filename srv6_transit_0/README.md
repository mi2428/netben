うごきません

### host
```
% ip -Version
ip utility, iproute2-ss180129
```

### R1
```
% docker exec -it R1 ip -6 r
2001:10::/64 dev net0 proto kernel metric 256 pref medium
unreachable fc00:1::/64 dev lo proto kernel metric 256 error -101 pref medium
fc00:2::/64 via 2001:10::3 dev net0 metric 1024 pref medium
fc00:3::/64 via 2001:10::3 dev net0 metric 1024 pref medium
fd00:1::/64 dev net1 proto kernel metric 256 pref medium
fd00:2::2  encap seg6 mode inline segs 3 [ fc00:3::1 fc00:2::1 :: ] dev net0 metric 1024 pref medium
fe80::/64 dev net0 proto kernel metric 256 pref medium
fe80::/64 dev net1 proto kernel metric 256 pref medium
```

### E1
```
04:13:34.903345 IP6 2001:10::1 > fc00:3::1: srcrt (len=6, type=4, segleft=2[|srcrt]
```

### R2
```
04:13:34.903367 IP6 2001:10::1 > fc00:2::1: srcrt (len=6, type=4, segleft=1[|srcrt]
```

### C2
```
04:13:34.903384 IP6 2001:10::1 > fd00:2::2: srcrt (len=6, type=4, segleft=0[|srcrt]
```
