# 基于docker的discuz镜像
discuz!X3.2

1、启动mysql实例

docker run --name your-mysql -e MYSQL_ROOT_PASSWORD=youpwd -d mysql

2、启动discuz实例

docker run --name your-discuz --link your-mysql:mysql -p 80:80 -d skyzhou/docker-discuz
