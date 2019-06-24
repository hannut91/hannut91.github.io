---
title: MYSQL 데이터베이스 User 추가하기
subTitle: MYSQL 데이터베이스 User 추가하기
category: 
tags: 
createdat: 2019-06-24 23:45:00
updatedat: 2019-06-25 00:23:39
---

## Create database

```bash
CREATE DATABASE database;
```

## Create user

```bash
CREATE USER 'userID'@'localhost' IDENTIFIED BY 'userPassword';
```

## Grant

```bash
GRANT DELETE, INSERT, SELECT, UPDATE ON database.* TO `user`@`host`;
```
