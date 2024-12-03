---
sidebar_position: 1
---

# Multi Node

Before you add new worker, you need to login to registry first by executing this command

```sh
mager registry:login <username> <server>
```

If you are using docker hub you can opt out server argument. Or previously you have login you can pass `-n` option to just only send credentials to manager node.

You can add worker after you have initialized namespace, by executing command below

```sh
mager worker:add <namespace>
```

It will ask you server credentials and it will run provisioning script. You can add as many as many node you want there is no limitation for it, however currently **Mager** still not support deploying service to specific node.

