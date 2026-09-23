# Awesome Agent First [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Software designed to be used by AI agents and by people, with the agent interface built in rather than bolted on.

Agent-first software is built so that an autonomous agent can operate it directly, reaching everything a person can reach. It is a *producer*: it exposes capability, and an agent consumes it. The software gains no agency of its own. What makes it agent-first is how it exposes itself: a machine-callable interface that is a primary way in rather than an afterthought, a model that describes itself at runtime, and data that stays with the operator rather than the vendor.

Agent-first is not agent-only. "First" is a claim about priority, in the way *mobile-first* never meant "no desktop". The test is that an agent can configure and run the software without the admin interface, while a person still has one: not needed, but still provided. Software that shuts people out is recorded separately in [agent-only.md](agent-only.md), and every candidate assessed but not listed, with the reason and what would change it, is in [considered.md](considered.md).

**Scope.** This list covers the producer side: software that an agent operates. It does not cover agents themselves, or the frameworks, orchestrators and SDKs used to build them. Adjacent lists are under [Related Lists](#related-lists). Every listed piece of software must meet [four inclusion clauses](contributing.md#gate-one-the-definition) and clear [a separate quality bar](contributing.md#gate-two-the-quality-bar), both spelled out there. The last two sections are reference material rather than entries: they hold the standards the clauses refer to, and the rubrics and writing worth reading. Only gated software entries carry tags.

**Disclosure.** This list is maintained by the author of Semantius, listed under Data Platforms in its normal category slot, in the same format as every other entry, and held to the same two gates.

## Contents

- [Customer Relationship Management (CRM)](#customer-relationship-management-crm)
- [Content Management](#content-management)
- [Localization](#localization)
- [Document Sharing](#document-sharing)
- [Enterprise Resource Planning (ERP)](#enterprise-resource-planning-erp)
- [Commerce](#commerce)
- [Project and Work Management](#project-and-work-management)
- [Scheduling](#scheduling)
- [Data Platforms](#data-platforms)
- [Communication Systems](#communication-systems)
- [Secrets and Access Management](#secrets-and-access-management)
- [Workflow Automation](#workflow-automation)
- [Monitoring and Incident Response](#monitoring-and-incident-response)
- [Standards](#standards)
- [Assessment and Reading](#assessment-and-reading)

## Customer Relationship Management (CRM)

- [ANOSF CRM](https://github.com/anosf/crm) - Self-hosted CRM whose web interface, REST API, MCP server and CLI all call one service layer, so every caller shares a permission model, an audit trail and a reversible change history. (`MIT`, `self-host`, `MCP`, `CLI`, `UI`)
- [Comp AI CRM](https://github.com/trycompai/crm) - Self-hosted CRM that republishes every tRPC procedure as a documented REST endpoint through a generated OpenAPI document, sharing one set of validation, middleware and services with the web interface, with workspace API keys for programmatic callers. (`MIT`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Headless CRM](https://github.com/Cam-Smith-One/Headless_CRM) - MCP-native CRM with a REST API, role-scoped access, webhooks on record changes and a minimal responsive interface. Self-described as early beta. (`AGPL-3.0`, `self-host`, `MCP`, `REST`, `UI`)
- [Twenty](https://twenty.com) - CRM whose metadata API creates objects, fields and relations and then the roles that govern them, with object, field and row-level permissions set through the same mutations its settings screens call, an OpenAPI document generated from your own workspace and a built-in MCP endpoint. ([Source Code](https://github.com/twentyhq/twenty)) (`AGPL-3.0 core`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Content Management

- [Contentful](https://www.contentful.com) - Content platform whose Content Management API defines content types, editor interfaces, locales and custom roles rather than only filling them, with a first-party MCP server covering the same surface and a web app that is a client of that API. (`hosted`, `REST`, `MCP`, `UI`)
- [Storyblok](https://www.storyblok.com) - Content platform whose Management API defines components and their fields, served to agents by a first-party hosted MCP endpoint with OAuth sign-in and tokens scoped to the spaces and permissions a caller needs, alongside a visual editor for people. (`hosted`, `REST`, `MCP`, `UI`)
- [Webiny](https://www.webiny.com) - Self-hosted headless CMS whose Manage GraphQL API creates, updates and deletes content models and their fields, so its admin area is a client of the same schema an agent calls, with API keys scoped to the same permissions. ([Source Code](https://github.com/webiny/webiny-js)) (`MIT core`, `self-host`, `GraphQL`, `UI`)

## Localization

- [Tolgee](https://tolgee.io) - Localization platform whose REST API creates projects, languages, namespaces and keys and sets each member's permission by scope and by language, described by an OpenAPI document the running server generates, with more than forty filters and a search parameter over translations. ([Source Code](https://github.com/tolgee/tolgee-platform)) (`Apache-2.0 core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Document Sharing

- [Papermark](https://www.papermark.com) - Document sharing and data room platform whose REST API creates data rooms, viewer groups, group members and per-document permissions rather than only handing out links, with a first-party CLI and MCP server, OAuth 2.1 tokens carrying scopes and full-text search across documents. ([Source Code](https://github.com/mfts/papermark)) (`AGPL-3.0 core`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Enterprise Resource Planning (ERP)

- [Odoo](https://www.odoo.com) - ERP whose external API creates models, fields and access rights through the same meta-models its own web client reads, documented by Odoo as altering models and fields on the fly, with `fields_get` returning every field's label, help text and type at runtime. ([Source Code](https://github.com/odoo/odoo)) (`LGPL-3.0`, `self-host`, `RPC`, `UI`)

## Commerce

- [Saleor](https://saleor.io) - Headless commerce platform whose GraphQL API creates product types, attributes, channels and permission groups rather than only reading them, with a dashboard built on that same schema and apps issued scoped tokens that are revocable independently of any person. ([Source Code](https://github.com/saleor/saleor)) (`BSD-3-Clause`, `self-host`, `GraphQL`, `MCP`, `UI`)

## Project and Work Management

- [Plane](https://plane.so) - Work tracking and wiki platform whose REST API defines work item types, custom properties, states and member roles rather than only filling them, with a first-party MCP server of 28 tools governed by the same permissions and a query language for filtering. ([Source Code](https://github.com/makeplane/plane)) (`AGPL-3.0 core`, `self-host`, `MCP`, `REST`, `UI`)

## Scheduling

- [Cal.com](https://cal.com) - Scheduling platform whose v2 API defines organization roles and the permissions inside them, member attributes and per-event booking questions rather than only booking against them, published as an OpenAPI document of more than two hundred paths, with OAuth clients and managed users for programmatic callers. (`hosted`, `REST`, `OpenAPI`, `UI`)

## Data Platforms

- [Busabase](https://busabase.com) - Local-first workspace where bases, fields, views, records and docs are all reachable through an MCP server, a generated OpenAPI document and a CLI, with credentials that can be capped so an agent's material writes wait as reviewable change requests. ([Source Code](https://github.com/busabase/busabase)) (`MIT`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [Directus](https://directus.com) - Maps an existing SQL database to REST and GraphQL APIs that the admin interface itself consumes, publishes an OpenAPI document and GraphQL SDL generated from your own schema, and governs its MCP server with the same permission model. ([Source Code](https://github.com/directus/directus)) (`MSCL-1.0`, `self-host`, `MCP`, `REST`, `UI`)
- [Semantius](https://www.semantius.com) - Puts role-based permissions and business logic inside PostgreSQL using row-level security, then generates the interface from that same model, so adding a table gives people working screens with no frontend code. ([Source Code](https://github.com/semantius/semantius)) (`MIT`, `self-host`, `SQL`, `CLI`, `UI`)

## Communication Systems

- [AgentMail](https://www.agentmail.to) - Provisions a durable email inbox per agent over a REST API, delivers inbound mail as structured JSON with search across threads, and serves the same mailbox over IMAP and SMTP. (`hosted`, `REST`, `MCP`, `IMAP`)
- [AgenticMail](https://github.com/agenticmail/agenticmail) - Self-hosted email, SMS and voice platform giving each agent its own address, number and scoped key, with a bundled Stalwart mail server so the same mailbox opens in any IMAP client, and a web interface served by the same API the agents call. (`MIT`, `self-host`, `MCP`, `IMAP`, `UI`)
- [Chimely](https://github.com/dodopayments/chimely) - Self-hostable in-app notification inbox in Rust and PostgreSQL whose committed OpenAPI covers environment creation, HMAC rotation and user management, so its operator dashboard is a client of the same API, alongside a drop-in inbox component for recipients. (`AGPL-3.0`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Hook0](https://www.hook0.com) - Webhooks as a service whose REST API creates organizations and the roles inside them, applications, event types, subscriptions and attenuable service tokens, so the dashboard and the subscriber portal are both clients of the OpenAPI document the server publishes, alongside a first-party CLI and MCP server. ([Source Code](https://github.com/hook0/hook0)) (`SSPL-1.0`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [Novu](https://novu.co) - Notification infrastructure whose API defines workflows, layouts, translations and provider integrations rather than only triggering them, published as a live OpenAPI document, with a dashboard for operators and an inbox component for recipients. ([Source Code](https://github.com/novuhq/novu)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Secrets and Access Management

- [Infisical](https://infisical.com) - Secrets, PKI, KMS and privileged access platform where machine identities are first-class and revocable independently of any person, and custom roles and permissions are creatable through a published OpenAPI document of over 1,500 paths. ([Source Code](https://github.com/Infisical/infisical)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Workflow Automation

- [Activepieces](https://www.activepieces.com) - Workflow automation whose first-party MCP server creates flows, steps, tables, fields and records under OAuth with protected-resource metadata and semantic search over its action catalog, alongside a REST API and the builder people use for the same work. ([Source Code](https://github.com/activepieces/activepieces)) (`MIT core`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [n8n](https://n8n.io) - Self-hostable workflow automation whose public API creates and updates workflows, credentials, projects, roles, users and data-table columns rather than a subset of them, generated from an OpenAPI specification. ([Source Code](https://github.com/n8n-io/n8n)) (`fair-code`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Monitoring and Incident Response

- [Keep](https://www.keephq.dev) - Alert and incident platform whose API creates roles, permissions, groups, users and scoped API keys as well as workflows, provider integrations and deduplication rules, with an OpenAPI document served by the running instance and expression-based search across alerts. ([Source Code](https://github.com/keephq/keep)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Standards

The discovery and identity surfaces that clauses 6 and 7 refer to: what software publishes about itself, so a caller needs no out-of-band instructions, and how an agent comes to hold its own credentials. Adoption across sixteen origins is measured in [discovery-survey.md](discovery-survey.md).

- [Agent Auth Protocol](https://agentauthprotocol.com) - Draft open standard giving each agent its own keypair, scoped capabilities and revocation independent of a human session, advertised through a well-known discovery document. ([Source Code](https://github.com/better-auth/agent-auth-protocol))
- [Agent Skills](https://agentskills.io) - Index format listing the tasks a service supports, served at a well-known path.
- [Better Auth Agent Auth](https://better-auth.com/docs/plugins/agent-auth) - Reference implementation of the Agent Auth Protocol, issuing per-agent credentials and human approval flows on top of an existing authentication server.
- [llms.txt](https://llmstxt.org) - Convention for a plain-text file at the site root that points a model-driven caller at the documentation that matters.
- [Model Context Protocol](https://modelcontextprotocol.io) - Protocol for exposing tools, resources and prompts to a calling model, including server cards that describe a server before it is connected.
- [OAuth 2.0 Authorization Server Metadata](https://www.rfc-editor.org/rfc/rfc8414.html) - RFC 8414, the document that lets a caller discover endpoints, grant types and scopes without being configured for them.
- [OAuth 2.0 Protected Resource Metadata](https://www.rfc-editor.org/rfc/rfc9728.html) - RFC 9728, the document by which an API names its authorization server and the scopes it accepts.
- [OpenAPI Specification](https://www.openapis.org) - Machine-readable description of an HTTP interface, its operations and its schemas.

## Assessment and Reading

- [Agent Readiness Score](https://isitagentready.com) - Scores a public origin from 0 to 100 across discoverability, content, bot access control and agent capabilities. ([Announcement](https://blog.cloudflare.com/agent-readiness/))
- [Agents First](https://agentsfirst.dev) - Design framework stating nine implementation principles and a level scale, with published scores for named sites.
- [Code Execution with MCP](https://www.anthropic.com/engineering/code-execution-with-mcp) - Argues that loading tool definitions and passing intermediate results through the model imposes a context ceiling, and that calling tools as code avoids it.
- [Resend auth.md](https://resend.com/auth.md) - A credential-acquisition document addressed to agents in the second person, stating plainly which flows are and are not supported.

## Related Lists

- [awesome-agent-native-services](https://github.com/haoruilee/awesome-agent-native-services) - Agent-native services and runtime infrastructure: email, browsers, memory, sandboxes, payments and MCP tools.
- [awesome-agent-first-tools](https://github.com/facundofarias/awesome-agent-first-tools) - Tools whose primary consumer is an agent rather than a person.
- [awesome-native-agent-platforms](https://github.com/sandbaseai/awesome-native-agent-platforms) - Runtimes, sandboxes, browsers, model routers and protocols for running agents in production.
- [awesome-agent-native-social](https://github.com/ColonistOne/awesome-agent-native-social) - Social platforms that admit agents as first-class users.
- [awesome-agent-experience](https://github.com/alexngai/awesome-agent-experience) - Tools and projects for making systems agent-friendly.
- [awesome-ai-agents](https://github.com/e2b-dev/awesome-ai-agents) - The consumer side: autonomous agents themselves.

## Contributing

[Contributions are welcome](contributing.md). Read the inclusion clauses and the quality bar first, because an entry has to clear both.

## Footnotes

Entries are checked against each project's own documentation, source or a live response, and every check is dated. Facts go stale and mistakes get made. If something here is wrong about your project, open an issue or a pull request with a link to what shows otherwise, and it will be corrected quickly. The same applies to `considered.md` and `agent-only.md`, linked above, where the reasoning for not listing something is written down.
