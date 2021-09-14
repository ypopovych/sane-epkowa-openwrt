![GITHUB-BADGE](https://github.com/ypopovych/sane-epkowa-openwrt/actions/workflows/build.yml/badge.svg)
# Epson Epkowa SANE backend for OpenWRT
This repository contains OpenWRT package for the Epson Epkowa Backend project at https://github.com/ypopovych/sane-epkowa
## Usage
### Download OpenWRT SDK
The easiest way is to use Docker image\
https://hub.docker.com/r/openwrtorg/sdk
### Prepare
Add repository
```
echo "src-git epkowa https://github.com/ypopovych/sane-epkowa-openwrt.git" >> feeds.conf.default
```

Update feeds
```
./scripts/feeds update base packages epkowa && make defconfig && ./scripts/feeds install sane-epkowa
```
### Compile
```
make package/sane-epkowa/compile V=s -j <CORES_NUM>
```

### Install
1) Copy package to temp folder on your router
```
scp bin/packages/<ARCH>/epkowa/sane-epkowa_<VERSION>.ipk root@<YOUR_ROUTER_IP>:/tmp
```
2) Login via ssh
```
ssh root@<YOUR_ROUTER_IP>
```
3) Install package via opkg
```
opkg install /tmp/sane-epkowa_<VERSION>.ipk
```

### Configure
You can edit configuration here\
```/etc/sane.d/epkowa.conf```

