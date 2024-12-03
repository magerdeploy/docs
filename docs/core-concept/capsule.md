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

**NOTE!!** Currently you only can use existing image in public repository for Capsule
