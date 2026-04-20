# releasejet-demo-multi-customer

A live demo of [**ReleaseJet**](https://www.releasejet.dev) running on a real multi-customer repo.

## What this shows

One GitHub repo, three customer tracks, three distinct release note streams:

| Customer | Tags | Latest release |
|---|---|---|
| Mercury | `mercury-v1.0.0` → `mercury-v1.2.0` | [mercury-v1.2.0](../../releases/tag/mercury-v1.2.0) |
| Jupiter | `jupiter-v1.0.0` → `jupiter-v1.2.0` | [jupiter-v1.2.0](../../releases/tag/jupiter-v1.2.0) |
| Neptune | `neptune-v1.0.0` → `neptune-v1.0.1` | [neptune-v1.0.1](../../releases/tag/neptune-v1.0.1) |

Every release page you see under **[Releases →](../../releases)** was generated automatically by a GitHub Action that runs:

    releasejet generate --tag <tag> --publish

on every tag push. No hand-editing. No commit-message conventions. Just labels on issues.

## How ReleaseJet does it

Our `.releasejet.yml` says which prefix belongs to which customer:

```yaml
clients:
  - prefix: mercury
    label: CUSTOMER-MERCURY
  - prefix: jupiter
    label: CUSTOMER-JUPITER
  - prefix: neptune
    label: CUSTOMER-NEPTUNE
```

When we tag `mercury-v1.2.0`, ReleaseJet only pulls closed issues with the `CUSTOMER-MERCURY` label that were closed between `mercury-v1.1.0` and `mercury-v1.2.0`. Other customers' issues never leak in.

## Want this for your repo?

- Install: `npm install -g @makispps/releasejet`
- Docs: https://www.releasejet.dev
- Source: https://github.com/makisp/releasejet
