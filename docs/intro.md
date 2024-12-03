---
slug: /
sidebar_position: 1
---

# Overview

**Mager** based on **Docker Swarm** architecture, **Mager** create preconfigured http proxy in order to serve http request.
So you just need to focus developing your application and Mager Deploy will handle deployment and scaling with single command.

**Mager** use [Traefik](https://traefik.io/) proxy to serve incoming http request and it will route to user container based on rule that defined in **mager.yaml**

It also **dev** preview, it will deploy http proxy and your service locally, so you can test deployment on your local machine first before you deploy to production server.
