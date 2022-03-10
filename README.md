# x-ui
Support multi-protocol multi-user XRAY panel

# Features
- System status monitoring
- Support multi-user multi-protocol, web-visual operation
- Supported protocol: Vmess, Vless, Trojan, Shadowsocks, Dokodemo-Door, Socks, HTTP
- Support Configuration More Transmission Configuration
- Traffic statistics, limited traffic, limit expiration time
- Customize XRAY Configuration Template
- Support HTTPS access panel (self-supplied domain name + SSL certificate)
- More advanced configuration items, see panels for details

# Installation & upgrade
```
bash <(curl -Ls https://raw.githubusercontent.com/vaxilu/x-ui/master/install.sh)
```

## Manual Installation & Upgrade
1. First download the latest compression package from https://github.com/vaxilu/x-ui/releases, generally choose the `AMD64` Architecture
2. Then upload this compressed package to the server's `/root/` directory and use the `root` user login server

> If your server CPU architecture is not `AMD64`, replace the` AMD64 in the command to other architectures

```
cd /root/
rm x-ui/ /usr/local/x-ui/ /usr/bin/x-ui -rf
tar zxvf x-ui-linux-amd64.tar.gz
chmod +x x-ui/x-ui x-ui/bin/xray-linux-* x-ui/x-ui.sh
cp x-ui/x-ui.sh /usr/bin/x-ui
cp -f x-ui/x-ui.service /etc/systemd/system/
mv x-ui/ /usr/local/
systemctl daemon-reload
systemctl enable x-ui
systemctl restart x-ui
```

## Installation using Docker

> This Docker tutorial is provided by [chasing66](https://github.com/chaasing66)

1. Install Docker
```shell
curl -fsSL https://get.docker.com | sh
```
2. Install X-UI
```shell
mkdir x-ui && cd x-ui
docker run -itd --network=host \
    -v $PWD/db/:/etc/x-ui/ \
    -v $PWD/cert/:/root/cert/ \
    --name x-ui --restart=unless-stopped \
    enwaiax/x-ui:latest
```
>Build Own mirror
```shell
docker build -t x-ui .
```

## Suggestion system
- CentOS 7+
- Ubuntu 16+
- Debian 8+

# common problem

## Migrate from V2-UI
First install the latest version of the X-UI on the server installed in the V2-UI, then use the following command to migrate, will migrate this machine V2-UI's `All Inbound account data` to X-UI, `panel settings, and username passwordWill not migrate`
> After the migration is successful, please close the `V2-UI` and `Restart the X-UI`, otherwise the V2-UI's Inbound will generate a port conflict with the X-UI inbound`
```
x-ui v2-ui
```

## issue close
Various small white problems have high blood pressure

## Stargazers over time

[![Stargazers over time](https://starchart.cc/vaxilu/x-ui.svg)](https://starchart.cc/vaxilu/x-ui)
