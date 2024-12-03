---
sidebar_position: 4
---

# Deploy To Production

In order to deploy to production you have to create [Namespace](http://test) first.

```sh
mager namespace:add
```

It will prompt you several question like first server credentials,. You need only run this once. Make sure you have have sudo without password access for your ssh key. It will **Mager** will do provisioning for you such as install docker and setup firewall.

To deploy you need to run

```sh
mager deploy <namespace>
```

It will build image locally and upload via ssh, for single server setup no registry are required. If you wish to deploy to multinode or preview deployment in staging you can check on advanced section.
