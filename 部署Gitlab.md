## 安装Docker
### 删除就版本的Docekr
>$ sudo apt-get remove docker docker-engine docker.io

### 更新Doceker仓库
1. Update the apt package index:
>$ sudo apt-get update

2. Install packages to allow apt to use a repository over HTTPS:
>$ sudo apt-get install \
>apt-transport-https \
>ca-certificates \
>curl \
>software-properties-common

3. Add Docker’s official GPG key:
>$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
>
>$ sudo apt-key fingerprint 0EBFCD88
>
>pub		4096R/0EBFCD88 2017-02-22
>
>​		Key fingerprint = 9DC8 5822 9FC7 DD38 854A E2D8 8D81 803C 0EBF CD88
>
>uid 		Docker Release (CE deb) <docker@docker.com>
>sub		4096R/F273FCD8 2017-02-22

### 安装Docker
1. Update the apt package index.
>$ sudo apt-get update

2. Install the latest version of Docker CE, or go to the next step to install a specific version. Any existing installation of Docker isreplaced.

>$ sudo apt-get install docker-ce

## 部署Gitlab

```shell
sudo docker run --detach \
--hostname 192.168.30.16 \
--publish 443:443 --publish 80:80 --publish 22:22 \
--name gitlab \
--restart always \
--volume /srv/gitlab/config:/etc/gitlab \
--volume /srv/gitlab/logs:/var/log/gitlab \
--volume /srv/gitlab/data:/var/opt/gitlab \
gitlab/gitlab-ce:latest

注意： ip地址需要改成本机的IP地址，还需要修改ssh的端口
```