### 1.新建Docker打包文件

```
vim /opt/docker/phpIPAM/docker-compose.yml**
```



### 2.将以下配置保存并编辑为docker-compose.yml

```yaml
# WARNING: Replace the example passwords with secure secrets.
# WARNING: 'my_secret_phpipam_pass' and 'my_secret_mysql_root_pass'

version: '3'

services:
  phpipam-web:
    image: phpipam/phpipam-www:latest
    ports:
      - "80:80"
    environment:
      - TZ=Europe/London
      - IPAM_DATABASE_HOST=phpipam-mariadb
      - IPAM_DATABASE_PASS=my_secret_phpipam_pass
      - IPAM_DATABASE_WEBHOST=%
    restart: unless-stopped
    volumes:
      - phpipam-logo:/phpipam/css/images/logo
      - phpipam-ca:/usr/local/share/ca-certificates:ro
    depends_on:
      - phpipam-mariadb

  phpipam-cron:
    image: phpipam/phpipam-cron:latest
    environment:
      - TZ=Europe/London
      - IPAM_DATABASE_HOST=phpipam-mariadb
      - IPAM_DATABASE_PASS=my_secret_phpipam_pass
      - SCAN_INTERVAL=1h
    restart: unless-stopped
    volumes:
      - phpipam-ca:/usr/local/share/ca-certificates:ro
    depends_on:
      - phpipam-mariadb

  phpipam-mariadb:
    image: mariadb:latest
    environment:
      - MYSQL_ROOT_PASSWORD=my_secret_mysql_root_pass
    restart: unless-stopped
    volumes:
      - phpipam-db-data:/var/lib/mysql

volumes:
  phpipam-db-data:
  phpipam-logo:
  phpipam-ca:
```

3.进入目标并启动容器

```
cd /opt/docker/phpIPAM/

```

从同一目录运行容器

```
docker-compose up -d`
```

