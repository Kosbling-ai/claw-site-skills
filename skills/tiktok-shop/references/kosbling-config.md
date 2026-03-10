# Kosbling Store Configuration

## Stores

| Store | Region | Profile | Port | Color | Credentials | Entry URL |
|-------|--------|---------|------|-------|-------------|-----------|
| KosblingDiyShop | 🇺🇸 US | `kosbling` | 18802 | 🩷 Pink | `secrets/tiktok-shop.enc` | `https://seller-us.tiktok.com` |
| KosblingDIY | 🇯🇵 JP | `kosbling-jp` | 18804 | 🔴 Red | `secrets/tiktok-shop-jp.enc` | `https://seller-jp.tiktok.com` |

## Credential Decryption

```bash
openssl enc -aes-256-cbc -d -salt -pbkdf2 -pass file:secrets/.keyfile -in secrets/<file>.enc
```

Output format: `{"service":"...","username":"...","password":"...","note":"..."}`

## Profile Rules

- ❌ Never use `openclaw` (18800) — RippleArk
- ❌ Never use `x-ops` (18801) — X ops agent
- ❌ Never use `playwhat` (18803) — PlayWhat agent

## JP Store Notes

- Currency: 円 (JPY)
- Customer messages typically in Japanese
- CS agent role: Customer Service5741
- Store health status tracked separately from US
