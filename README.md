# Workflow Automation

The common workflow-automation vocabulary -- the workflows people build, the triggers that start them, the runs that execute them and the connections to other apps they act through -- distilled from the APIs that already exist. CI/CD pipelines belong to their own context. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Workflow Automation, iPaaS, Integration Platform, No-Code, Low-Code, Workflows, Automation Platform, Integration in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| workflow | 73 | 59 | id 78%, name 76%, status 59%, description 51% | workflows 44, flows 12, automations 9, automation 5 |
| workflow_run | 35 | 31 | id 71%, status 71% | runs 17, executions 16, history 3, jobs 2 |
| trigger | 18 | 14 | type 64%, id 57% | triggers 13, trigger 6 |
| connection | 19 | 15 | id 93%, name 73%, app 67%, created_at 60%, status 60% | connections 12, credentials 8, integrations 1, connection 1 |

Cohort: 348 providers with harvested OpenAPI, 73 crosswalks. Of the providers exposing a workflow: 60% create, 77% list, 73% fetch, 47% update, 49% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- A workflow agrees on id, name, status and description across iPaaS platforms, no-code builders, RPA tools and AI-agent orchestrators -- Zapier's zaps, Make's scenarios and n8n's workflows are one concept.
- A connection agrees on id, name, the app it connects, status and created_at: the credential-to-an-app is the most uniform resource in integration platforms.
- A run agrees only on id and status: what a run records (steps, logs, errors) is the platform's own.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- The bare Automation tag is not used: it covers industrial automation and RPA hardware.
- A workflow covers flows, scenarios, zaps, automations, recipes and playbooks; CI pipelines are the CI/CD context's.
- Runs are `/workflow-runs` (CI/CD owns `/runs`); singular `/run` and `/execution` are actions and do not count.
- Credentials, authorizations and connected accounts are connections.
- Duplicates merged: Albato, Ethena, Webflow.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
