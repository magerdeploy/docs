---
sidebar_position: 4
---

# Capsule

Capsule is third party outside your service scope that can installed in your namespace. For example database and application to support your service. Capsule that have installed in your namespace are categorized as `service` so you can manage them also.

Capsule can be installed with this command.

```sh
mager install https://github.com/magerdeploy/capsule-db-mysql
```

Capsule concept was designed to be decentralized and easy to install. You can also install it from your local

```sh
mager install file://~/capsule/mysql
```

Same as service Capsule will be installed on manager node on single server and on worker node when on multi node

**NOTE!!** Currently you only can use existing image in public repository for Capsule

## Creating Capsule

Basically creating capsule is same with creating service, you have create `mager.yaml` the only different for now capsule dont have build process, so Image must be available in registry first.

Sample capsule definition

```yaml title=mager.yaml
db-mysql:
  build:
    image: mysql:{$MYSQL_VERSION:-latest}
  config:
    - config/my.cnf:/etc/mysql/conf.d/my.cnf
  volumes:
    - mysql:/var/lib/mysql
  env:
    MYSQL_ROOT_PASSWORD: "${MYSQL_ROOT_PASSWORD:-changeme!}"
    MYSQL_DATABASE: "${MYSQL_DATABASE:-your_db}"
    MYSQL_USER: "${MYSQL_DATABASE:-mager}"
    MYSQL_PASSWORD: "${MYSQL_PASSWORD:-changeme!}"
```
