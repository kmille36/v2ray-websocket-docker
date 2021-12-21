# v2ray-websocket-docker
V2ray server for ubuntu docker ( for centos replace apt with yum)

Supported architectures (more info): amd64, arm32v6, arm32v7, arm64v8, i386, ppc64le, s390x

```console 
sudo apt update
sudo apt install -y docker docker.io
sudo docker pull teddysun/v2ray
sudo mkdir -p /etc/v2ray
sudo cat > /etc/v2ray/config.json <<EOF
{
  "inbounds": [
  {
    "port": 80,
    "protocol": "vmess",
    "settings": {
      "clients": [
        {
          "id": "ba651c8c-cb35-4c46-bf6c-f90bd6f094e3",
          "alterId": 64
        }
      ]
    },
    "streamSettings": {
      "network": "ws"
    }
  }
  ],
  "outbounds": [
  {
    "protocol": "freedom",
    "settings": {}
  }
  ]
}
EOF
sudo docker run -d -p 80:80 --name v2ray --restart=always -v /etc/v2ray:/etc/v2ray teddysun/v2ray
```



