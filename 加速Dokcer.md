### 安装／升级你的Docker客户端

推荐安装`1.10.0`以上版本的Docker客户端。

您可以通过阿里云的镜像仓库下载：[docker-engine](http://mirrors.aliyun.com/help/docker-engine)、[docker-ce](http://mirrors.aliyun.com/help/docker-ce)

或执行以下命令：

```
curl -sSL http://acs-public-mirror.oss-cn-hangzhou.aliyuncs.com/docker-engine/internet | sh -

```

### 如何使用Docker加速器

#### 针对Docker客户端版本大于1.10的用户

您可以通过修改daemon配置文件`/etc/docker/daemon.json`来使用加速器：

```
sudo mkdir -p /etc/docker
sudo tee /etc/docker/daemon.json <<-'EOF'
{
  "registry-mirrors": ["https://ewikvryg.mirror.aliyuncs.com"]
}
EOF
sudo systemctl daemon-reload
sudo systemctl restart docker
```