---
sidebar_position: 2
---

# Mager Definition

Mager definition are yaml file that contain information that required by **Mager** to build and deploy your services. Mager definition can only contain 1 image, those image can be used in multiple service in same definition.

## Override Mager Definition

You can override Mager definition based on deployment environment. currently **Mager** support overriding definition for `dev` and `preview` environment.

To override you have to create de definition for example `mager.dev.yaml`, then you can override options from base `mager.yaml`

## Build Options

```yaml
build:
  image: someimage # required
  file: Dockerfile # optional
  target: frankenphp_prod # optional
  args: # optional
    SOME_ARGS:ARG
```

### Image

This image property are used to tag image that you have built, in multi node scenario **Mager** will use this properto to push the image so if you intent to use other registry to docker hub you have to enter this property properly e.g if you want to push image to github container registry to you have to enter image name as `ghcr.io/NAMESPACE/IMAGE_NAME`

### File

This property used to determine `Dockerfile` name, if you use any other name you need to specify in defintion.

### Target

You can target specific build using this property

### Args

Used to pass build argument in `Dockerfile`

## Service Options

Config similar to docker-compose but with additional configuration

```yaml
services:
  service-name:
    cmd: ['php', '-v']
    option:
      limit_cpu: 0.25
      limit_memory: 512MB
    execute_once:
      - echo '1'
    before_deploy:
      - echo '1'
    after_deploy:
      - echo '1'
    hosts:
      - host.docker.internal:host-gateway
    volumes:
      - ./:/app
    env:
      SERVER_NAME: ${SERVER_NAME:-:80}
      MERCURE_PUBLISHER_JWT_KEY: ${CADDY_MERCURE_JWT_SECRET:-!ChangeThisMercureHubJWTSecretKey!}
      MERCURE_SUBSCRIBER_JWT_KEY: ${CADDY_MERCURE_JWT_SECRET:-!ChangeThisMercureHubJWTSecretKey!}
      MERCURE_URL: ${CADDY_MERCURE_URL:-https://symfony-demo.wip/.well-known/mercure}
      MERCURE_PUBLIC_URL: ${CADDY_MERCURE_PUBLIC_URL:-https://symfony-demo.wip/.well-known/mercure}
      MERCURE_JWT_SECRET: ${CADDY_MERCURE_JWT_SECRET:-!ChangeThisMercureHubJWTSecretKey!}
    proxy:
      ports:
        - 80/tcp
      rule: Host(`{$host}`) && Path('/') # ${$host} is placeholder, it will replace by value of host attribute
      host: demo-app.com
```

### Execute Once

This options contain list of command that will executed on first deployment.

**NOTE!!** if you delete and deploy service again commands in `execute_once` will be executed

### Before Deploy

This executed after `executed_once` are executed and will executed each deployment.

### After Deploy

This executed after deployment success and pass health check.

### Proxy

This configuration needed when you need expose your service to internet. This configuration will pass to http proxy to route your services properly. `proxy.ports` is your service port, you dont need expose your service port! *Mager* was designed to make service never expose port to public, all http service must be proxied via Traefik.
