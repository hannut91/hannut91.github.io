---
title: Install mongodb
subTitle: ## With docker
category: 
tags: 
createdat: 2019-06-24 23:45:00
updatedat: 2019-06-24 23:45:00
---

```bash
$ docker run --name mongo_local -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=password -e -v /Users/yunseok/Documents/mongodb:/data/db -p 27017:27017 -d mongo:4.0.9
```
