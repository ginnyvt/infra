# Cloudflare Tunnel

This directory contains the configuration for the Cloudflare Tunnel.

## Overview

The Cloudflare Tunnel is a daemon that runs on the edge and establishes outbound connections to the Cloudflare network. It then proxies incoming requests to the origin server.

## Login

```bash
cloudflared login
```

## Create a Tunnel

To create a new tunnel, run the following command:

```bash
TUNNEL_NAME=harrytang-staging
cloudflared tunnel create $TUNNEL_NAME
```

## Create secret

```bash
kubectl -n $TUNNEL_NAME create secret generic tunnel-credentials --dry-run=client \
--from-file=credentials.json=/root/.cloudflared/3e3673b2-a52c-42a8-9dca-b69fa6df430e.json \
-o yaml | kubeseal --format=yaml > sealed-secret.yaml
```
