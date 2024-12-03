---
sidebar_position: 1
---

# Namespace

**Mager** use namespacing concept to create isolation between application. `Namespace` can contain as many as service and capsule you want, it will connected to same network, so you can communicate between services in same namespace using internale network. One or multinode can contain many `namespace` but services between namespace cant comunicate via internal docker network. In most usecase you will only need 2 namespace `local` and your project namespace, you can also treat namespace as development environment if you want you can easily replicate service or capsule installed from another `namespace` with minimum effort.

**NOTE!!** Each namespace will install http proxy to proxy your http based service.

## Local Namespace

Local Namespace are created when you do deployment preview on your local machine. Since by default http proxy will listen to port 80 and 443 it might need conflict with your current development tools so you need to disable them temporarily when deploy to your local machine.

To remove proxy to your local, you can delete entire namespace, it will delete all associated service also!

```sh
mager namespace:del local
```
