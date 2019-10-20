---
title: mariaDB
---

## Run MariaDB using [Docker](Docker)

```bash
docker run --name local-mariadb -e MYSQL_ROOT_PASSWORD=root1234 -p 3306:3306 -d mariadb:10.4.8
```

## Create Database

```sql
CREATE DATABASE <name>;
```