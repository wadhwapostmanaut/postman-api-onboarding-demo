# Demo Service Activation API: Postman Onboarding

This repo contains the automated Postman onboarding workflow for the Demo Service Activation API, a demo service that handles activation of mobile plans, broadband connections, and voice services against existing customer accounts.

---

## What the workflow does

The workflow is spec-driven. It reads the OpenAPI spec and uses it as the source for everything it provisions in Postman. When it runs, it creates a fully structured Postman workspace for this service:

- The OpenAPI spec, uploaded to Postman Spec Hub
- Three test collections: baseline (every endpoint), smoke (a quick health check), and contract (verifies the live API still matches the spec)
- Two environments, prod and staging, with the runtime URLs pre-configured
- A weekly monitor that runs the contract tests on a schedule to catch spec drift

It also registers the service in the Postman API Catalog and commits the generated collection and environment files back into this repo.

---

## How it runs

The workflow runs in two ways:

- Automatically, whenever the spec under `open-api-specs/` changes on the main branch
- Manually, from the Actions tab using the Run workflow button

---

## What's in this repo

- `open-api-specs/demo-service-activation-api-openapi.yaml` is the OpenAPI spec, the single source of truth for this service
- `.github/workflows/onboard.yml` is the workflow that reads the spec and provisions everything in Postman

---

## Per-service configuration

Only five values in the workflow file need to change per service: the project name, the domain, the domain code, the spec path, and the environment runtime URLs. Everything else stays the same.

---

## Required secrets

Three secrets must be set in the repo under Settings > Secrets and variables > Actions:

- `POSTMAN_API_KEY` for Postman operations
- `POSTMAN_ACCESS_TOKEN` for governance and workspace linking
- `GH_FALLBACK_TOKEN` for committing generated assets back to the repo

---

## Contact

Platform Engineering (Demo): platform-demo@example.com

---

> This is a demonstration service. The runtime URLs are placeholders and do not point to a live API.
