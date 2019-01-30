
DOCKER INSTALLATION
----------------------------------------------------------------------------------------------------------------------------------------

mkdir v2ray-agent  &&  cd v2ray-agent

curl https://raw.githubusercontent.com/alliswell2day/v2ray-mod/v2ray_api/install.sh -o install.sh && chmod +x install.sh && bash install.sh


-A INPUT -p tcp -m state --state NEW -m tcp --dport 4444 -j ACCEPT

-A INPUT -p tcp -m state --state NEW -m tcp --dport 4445 -j ACCEPT

docker-compose up -d

docker pull alliswell2day/v2ray_mod:api_alpine





STANDARD ( MANUAL ) INSTALLATION
----------------------------------------------------------------------------------------------------------------------------------------

CentOS 7

**install v2ray：**

curl -L -o /tmp/go.sh https://raw.githubusercontent.com/alliswell2day/v2ray-core/4.12.0_ips/release/install-release.sh && bash /tmp/go.sh -f --version 4.12.0

yum install -y https://centos7.iuscommunity.org/ius-release.rpm

yum update

yum install -y git python36u python36u-libs python36u-devel python36u-pip gcc


git clone -b v2ray_api https://github.com/alliswell2day/shadowsocks-munager.git

cd shadowsocks-munager

cp config/config_example.yml config/config.yml

cp config/config.json /etc/v2ray/config.json

pip3.6 install -r requirements.txt


**edit**

edit: /root/v2ray-mod/config/config.yml   set sspanel_url、key、node_id ,api_port 。

edit /etc/v2ray/config.json    line 12 same value as  api_port 。


-A INPUT -p tcp -m state --state NEW -m tcp --dport 4444 -j ACCEPT

-A INPUT -p tcp -m state --state NEW -m tcp --dport 4445 -j ACCEPT 


**RUN：**

screen -S v2ray

python3.6 run.py --config-file=config/config.yml



