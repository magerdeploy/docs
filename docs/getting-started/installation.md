---
sidebar_position: 1
---

# Requirement

Unix based OS, but currently only tested on `Ubuntu 24.04`

* Docker
* Mkcert (needed for generating TLS certificate for dev preview)
* cURL

```sh showLineNumbers title='install-requirement.sh'
DEBIAN_FRONTEND=noninteractive sudo apt-get update -y && sudo apt-get upgrade -y
sudo apt-get install ca-certificates curl wget git jq openssl mkcert libnss3-tools
curl -s https://releases.rancher.com/install-docker/27.0.3.sh | sh 2>&1
```

# Installing Mager

```sh title='install-requirement.sh'
curl https://raw.githubusercontent.com/praswicaksono/mager-deploy/refs/heads/master/install.sh | sh
```
