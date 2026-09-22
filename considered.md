# Considered, not listed

Every candidate assessed for this list that did not end up in the readme, why, and what would change that. Checked 2026-09-22.

This file exists because an inclusion rule nobody can see being applied is just a claim. Nothing here is a criticism of the software. Several of these are better built and more widely used than entries that did qualify, and a few fail on something as small as a missing licence file. "Not listed yet" is meant literally: say so in an issue when one of these changes and it gets re-checked.

The criteria are in [contributing.md](contributing.md). Software that fails clause 4 by design is recorded separately in [agent-only.md](agent-only.md), because being built agent-only is a decision rather than a shortfall.

**Corrections are welcome and will be made quickly.** Every claim here was checked against the project's own repository, documentation or a live response on the date given, and is a snapshot of what was public then. That method is fallible in three ways: a capability can exist somewhere the check did not look, undocumented behaviour is invisible to it, and everything here goes stale as projects ship. If something is wrong about your project, open an issue or a pull request with a link to what shows otherwise. Factual corrections are not argued with. Judgement calls, meaning whether a clause is the right clause, are worth discussing in the open, and that discussion belongs in an issue where everyone can read it.

## Fails a clause

- [Relaticle](https://github.com/relaticle/relaticle) - Fails clause 2. Custom field definitions are read-only everywhere they are reachable: the MCP server offers `list-custom-fields-tool` and `get-crm-schema-tool` with no write equivalent, `CustomFieldsController` implements only `index`, and no console command defines one. Creating a custom field requires the Filament admin panel, which is clause 2's "an API covering a subset of what the interface can do". **Would qualify with** a writable custom-fields endpoint or MCP tool.
- [Palantir Foundry Ontology](https://www.palantir.com/docs/foundry/ontology/overview) - Fails clause 2. Object, link and action types are created in Ontology Manager, and the platform API reads the ontology without being able to define it. Ontology-as-code through SuperRepos is a repository workflow a person deploys, not an interface an agent calls. **Would qualify with** the ontology modification endpoints Palantir has said are in progress.
- [Agentic Postgres](https://www.tigerdata.com/blog/postgres-for-agents) - Fails clause 4 under the audience test. Its human paths are psql, third-party SQL clients and the console SQL editor, which are database administration tools rather than interfaces for the people whose records live there. **Would qualify with** a shipped interface for working with the data as records.

## Fails the quality bar

Each of these meets enough of the definition to be worth re-checking. All four fail on licence or maintenance, which are the easiest things on this page to fix.

- [cluster-software/agent-crm](https://github.com/cluster-software/agent-crm) - No licence detected, last push 2026-06-05. The most adopted of the unlicensed candidates at 118 stars. **Would qualify with** a licence file.
- [keshav55/agent-crm](https://github.com/keshav55/agent-crm) - No licence detected, last push 2026-08-28, so actively worked on. **Would qualify with** a licence file.
- [agentsfirst](https://github.com/capitalthought/agentsfirst) - No licence detected on the repository, last push 2026-06-16. The framework it documents is still cited under Assessment and Reading, because reference material is not held to the software gates.
- [pg-mcp-server](https://github.com/stuzero/pg-mcp-server) - Last push 2025-09-10, beyond the six-month line, and a connector over PostgreSQL rather than a product.

## Out of scope

- [BigQuery](https://cloud.google.com/bigquery) - Meets the clauses and is excluded on curation. What makes it eligible, DDL, `GRANT` and `REVOKE`, row access policies and `INFORMATION_SCHEMA`, is equally true of Snowflake, Databricks, Redshift, ClickHouse and PostgreSQL itself, so admitting it admits every cloud database. Its agent-specific capability, BigQuery Graph, was in preview when this was checked. **Would qualify with** generally available capability built for agents rather than generic administrability.
- [Bonnard](https://bonnard.ai) - The agentic semantic layer assessed here was archived on 2026-07-03, and its repository now points to a different current product. That product, `@bonnard/mcp-charts`, is an SDK that "adds interactive charts to any MCP server". It fails clause 1: a library a developer embeds in their own server, which neither holds nor governs data of its own.
- **Cloudflare Workers and Vercel AI Gateway** - Runtime infrastructure an agent calls in passing rather than software holding an organization's records. Covered by the lists under Related Lists in the readme.

## No longer there

- **otomata-tech/headless-crm** - The repository returns 404.
