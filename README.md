# docker-lab

Docker CI/CD testing repository using `doco-cd` and `renovate`, with automated discovery

## Diagram

```mermaid
flowchart TD
    d["doco-cd"]
    r["Renovate"]
    a["Apps"]
    c["Caddy Reverse Proxy"]
    gh["Github"]
    u["User"]
    k["Uptime Kuma"]
    ak["Auto Kuma"]
    n["Apprise"]
    sl["Slack"]
    bws["Bitwarden Secrets Manager"]

    d -- Get Secrets --> bws
    d -- Poll For Changes --> gh
    u --> c --> a
    r -- Pull Request --> gh
    d -- Discover and deploy --> a
    d -- Trigger --> n -- Notify --> sl --> u
    ak -- Discover --> a
    ak -- Configure --> k
    k -- Monitor --> a
    d -- Discover and deploy --> k
    d -- Discover and deploy --> ak
    d -- Discover and deploy --> c



```

## Deployment

- Clone repository to host
- Create `.env` file
- Run `docker compose up -d` in `/doco-cd`

### Env file

```
TBD - bitwarden and slack secrets
```