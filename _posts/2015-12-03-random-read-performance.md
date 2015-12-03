---
layout: post
title: Random read performance depending on block size
categories: []
tags: []
status: publish
type: post
published: true
---

When designing systems that store data on disk, it's important to know how worthwile it is to batch reads into larger blocks.
The tests were conducted on AMD FX-6300 with 32 GB of RAM -- the results are from the second run, so data already in RAM shouldn't play imporant role here. [Test program](https://gist.github.com/zielmicha/c4ac8974d2f6a55bf548).

Seagate Barracuda ST2000DM001 HDD (2 TB):

```
bs=4k read=1557 size=6.0 MB speed=0.2 MB/s
bs=8k read=1576 size=12.0 MB speed=0.4 MB/s
bs=16k read=1547 size=24.0 MB speed=0.8 MB/s
bs=32k read=1564 size=48.0 MB speed=1.6 MB/s
bs=64k read=1510 size=94.0 MB speed=3.1 MB/s
bs=128k read=1513 size=189.0 MB speed=6.3 MB/s
bs=256k read=1357 size=339.0 MB speed=11.3 MB/s
bs=512k read=1262 size=631.0 MB speed=21.0 MB/s
bs=1024k read=1115 size=1115.0 MB speed=37.2 MB/s
bs=2048k read=895 size=1790.0 MB speed=59.6 MB/s
bs=4096k read=649 size=2596.0 MB speed=86.5 MB/s
bs=8192k read=432 size=3456.0 MB speed=115.0 MB/s
bs=16384k read=253 size=4048.0 MB speed=134.5 MB/s
bs=32768k read=111 size=3552.0 MB speed=117.5 MB/s
bs=65536k read=43 size=2752.0 MB speed=91.3 MB/s
bs=131072k read=32 size=4096.0 MB speed=135.4 MB/s
```

Crucial MX100 SSD (128 GB)

```
bs=4k read=294420 size=1150.0 MB speed=38.3 MB/s
bs=8k read=254689 size=1989.0 MB speed=66.3 MB/s
bs=16k read=198916 size=3108.0 MB speed=103.6 MB/s
bs=32k read=155193 size=4849.0 MB speed=161.7 MB/s
bs=64k read=106627 size=6664.0 MB speed=222.1 MB/s
bs=128k read=67619 size=8452.0 MB speed=281.7 MB/s
bs=256k read=34369 size=8592.0 MB speed=286.4 MB/s
bs=512k read=20897 size=10448.0 MB speed=348.3 MB/s
bs=1024k read=11857 size=11857.0 MB speed=395.2 MB/s
bs=2048k read=6340 size=12680.0 MB speed=422.6 MB/s
bs=4096k read=3350 size=13400.0 MB speed=446.6 MB/s
bs=8192k read=1689 size=13512.0 MB speed=450.4 MB/s
bs=16384k read=857 size=13712.0 MB speed=456.8 MB/s
bs=32768k read=240 size=7680.0 MB speed=255.3 MB/s
bs=65536k read=120 size=7680.0 MB speed=255.8 MB/s
bs=131072k read=62 size=7936.0 MB speed=260.1 MB/s
```
