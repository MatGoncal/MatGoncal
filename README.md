# Matheus Gonçalves

**Backend Engineer · Payments · PIX, cross-border, split**

I build payment systems: idempotent webhooks, FX rate locks, multi-currency balances, and settlement splits. Portfolio is a shared **AcmePay** API contract implemented across four stacks.

## AcmePay ecosystem

| Repo | Stack | Role |
|------|-------|------|
| [pix-wallet-api](https://github.com/MatGoncal/pix-wallet-api) | Laravel 12 · Postgres · Redis | PIX wallet API (Sail) |
| [partner-dashboard-vue](https://github.com/MatGoncal/partner-dashboard-vue) | Vue 3 · Pinia · Vite | Partner dashboard |
| [checkout-portal-next](https://github.com/MatGoncal/checkout-portal-next) | Next 15 · TanStack Query | Checkout + webhook simulator |
| [payment-api-nest](https://github.com/MatGoncal/payment-api-nest) | NestJS 11 · Prisma · BullMQ | Same contract, Nest side |

Pick any repo — the same OpenAPI 3.1 spec lives in `Docs/specs/`.

One contract, two backend implementations, one frontend on each:

```mermaid
graph TB
  Contract["API_CONTRACT.md / OpenAPI 3.1"]

  subgraph FE["Frontends"]
    Vue["partner-dashboard-vue<br/>Vue 3"]
    Next["checkout-portal-next<br/>Next 15"]
  end

  subgraph BE["Backends · same contract, two stacks"]
    Laravel["pix-wallet-api<br/>Laravel 12"]
    Nest["payment-api-nest<br/>NestJS 11"]
  end

  Contract -.->|implements| Laravel
  Contract -.->|implements| Nest
  Vue -->|HTTP| Laravel
  Next -->|HTTP| Nest
```

### Canonical endpoints

- `POST /v1/payments` — PIX cash-in (QR + copia-e-cola)
- `POST /v1/webhooks/payment` — idempotent provider events
- `POST /v1/fx/quotes` — rate lock (5 min)
- `GET /v1/balances` — multi-currency wallet
- `POST /v1/payouts` — async payout (debit on confirm)
- `POST /v1/payments/{id}/splits` — platform / seller / affiliate

Money is always **integer minor units** — never float.

## Focus

- Spec-driven delivery (`AGENTS.md` + `Docs/specs` before code)
- Fintech domain: settlement, idempotency, FX, split
- Laravel + Vue (hiring) and Nest + Next (marketplace / PagAmerican prep)

## Contact

- LinkedIn: [matheusgoncalvesweb](https://www.linkedin.com/in/matheusgoncalvesweb/)
- Email: matheus.gabryel10@gmail.com
