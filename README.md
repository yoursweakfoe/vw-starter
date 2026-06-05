[中文](./README.zh-CN.md) | English

## Step 1 — Install mkcert and Generate Certificates

```bash
# following script is for windows
# Install mkcert
winget install FiloSottile.mkcert

# Install local CA into Windows certificate trust store (one-time only)
mkcert -install

# Run from your project root — outputs certificates to nginx/certs/
mkcert -cert-file nginx/certs/cert.pem -key-file nginx/certs/key.pem vaultwarden.local localhost 127.0.0.1
```

## Step 2 — Configure the Hosts File

Add the following line:

```
127.0.0.1  vaultwarden.local
```

## Step 3 — Start the Services

```bash
docker compose up -d
```

## Step 4 — Configure the Browser Extension

In Bitwarden chrome extension's self-hosted server field, enter the following URL.

```
https://vaultwarden.local:8443
```

> **Note:** Port `8443` and `880` is used because the Docker Compose port mappings intentionally avoid the standard ports `80` and `443`.