# 基于docker的discuz镜像
discuz!X3.2

1、启动mysql实例

docker run --name your-mysql -e MYSQL_ROOT_PASSWORD=youpwd -d mysql

2、启动discuz实例

docker run --name your-discuz --link your-mysql:mysql -p 80:80 -d skyzhou/docker-discuz

# Docker-Compose 部署
```yaml
version: '3.1'
services:
  docker-discuz:
    restart: always
    image: skyzhou/docker-discuz:latest
    container_name: docker-discuz
    privileged: true
    ports:
      - 30002:80
    environment:
      MYSQL_PORT_3306_TCP: 134.134.2.67
      DISCUZ_DB_HOST: 134.134.2.67
      DISCUZ_DB_USER: root
      DISCUZ_DB_PASSWORD: 123456
      DISCUZ_DB_NAME: discuz
    volumes:
      - ./data:/var/www/html
```
