# Awesome Agent First [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Software that AI agents and people can both use fully, without the agent falling back to a browser.

Agent-first software can be used fully by an autonomous agent, within whatever access it has been given, without falling back to a browser. It is a *producer*: it exposes capability, and an agent consumes it. The software gains no agency of its own. What makes it agent-first is how it exposes itself: a machine-callable interface that covers everything a user does, and guidance from its vendor that tells an agent how to work in it. People get an app; agents get an interface they can run, and guidance that tells them how.

Agent-first is not agent-only. "First" is a claim about priority, in the way *mobile-first* never meant "no desktop". The test is that an agent can do its work without a browser, while a person still has an interface of their own: not needed by the agent, but still provided. Software that shuts people out is recorded separately in [agent-only.md](agent-only.md), and candidates that failed a clause or the quality bar, with the reason and what would change it, are in [considered.md](considered.md).

Always-on agents gain the most from agent-first software, because they work while nobody is watching. Grok Bot and Meta's Muse each get a cloud computer of their own, but mostly reach other software through its screens, signed in as a person: they act with all of that person's access, the software records their work as the person's, and their work breaks when a screen changes. Agent-first software gives such an agent an interface and guidance built for it, covering everything a user does rather than the records alone, and can give it a credential of its own, so the records name the agent and not the person. An MCP server that wraps part of a product helps only as far as it reaches, and the agent falls back to the screens for the rest.

**Scope.** This list covers the producer side: software that an agent operates. It does not cover agents themselves, or the frameworks, orchestrators and SDKs used to build them. Adjacent lists are under [Related Lists](#related-lists). Every listed piece of software must meet [the inclusion criteria](contributing.md#gate-one-the-definition) and clear [a separate quality bar](contributing.md#gate-two-the-quality-bar), both spelled out there. The last two sections are reference material rather than entries: they hold the standards the clauses refer to, and the rubrics and writing worth reading. Only gated software entries carry tags.

**Disclosure.** This list is maintained by the author of Semantius, listed under Data Platforms in its normal category slot, in the same format as every other entry, and held to the same two gates.

## Contents

- [Customer Relationship Management (CRM)](#customer-relationship-management-crm)
- [Customer Support](#customer-support)
- [Content Management](#content-management)
- [Knowledge Bases](#knowledge-bases)
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
- [Product Analytics](#product-analytics)
- [Standards](#standards)
- [Assessment and Reading](#assessment-and-reading)

## Customer Relationship Management (CRM)

- [ANOSF CRM](https://github.com/anosf/crm) - CRM whose REST API, MCP server and CLI share one service layer, with a reversible audit trail. (`MIT`, `self-host`, `MCP`, `CLI`, `UI`)
- [Comp AI CRM](https://github.com/trycompai/crm) - CRM designed for AI agents. (`MIT`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Headless CRM](https://github.com/Cam-Smith-One/Headless_CRM) - MCP-native, API-first CRM built for AI agents. (`AGPL-3.0`, `self-host`, `MCP`, `REST`, `UI`)
- [Planhat](https://www.planhat.com) - Customer platform for B2B commercial teams that brings customer data, collaboration and automation together across the customer lifecycle. (`hosted`, `REST`, `MCP`, `UI`)
- [Twenty](https://twenty.com) - Modular CRM built as an open alternative to Salesforce. ([Source Code](https://github.com/twentyhq/twenty)) (`AGPL-3.0 core`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Customer Support

- [Plain](https://www.plain.com) - Support platform for B2B teams that brings email, Slack, Microsoft Teams, chat, Discord and contact forms into one queue. (`hosted`, `GraphQL`, `MCP`, `UI`)

## Content Management

- [Contentful](https://www.contentful.com) - API-first composable content platform. (`hosted`, `REST`, `MCP`, `UI`)
- [Storyblok](https://www.storyblok.com) - Headless CMS with a visual editor. (`hosted`, `REST`, `MCP`, `UI`)
- [Strapi](https://strapi.io) - Headless CMS written in JavaScript and TypeScript. ([Source Code](https://github.com/strapi/strapi)) (`MIT core`, `self-host`, `MCP`, `REST`, `UI`)
- [Webiny](https://www.webiny.com) - Headless CMS that runs on AWS serverless services, with multi-tenancy. ([Source Code](https://github.com/webiny/webiny-js)) (`MIT core`, `self-host`, `GraphQL`, `UI`)

## Knowledge Bases

- [AgentDocs](https://agentdocs.eu) - Collaborative Markdown documentation platform where AI agents are first-class users. (`hosted`, `MCP`, `REST`, `UI`)

## Localization

- [Tolgee](https://tolgee.io) - Localization platform with in-app translation and collaborative tools. ([Source Code](https://github.com/tolgee/tolgee-platform)) (`Apache-2.0 core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Document Sharing

- [Fastio](https://fast.io) - Project workspaces that hold the files for a team and its AI agents. (`hosted`, `MCP`, `REST`, `CLI`, `UI`)
- [Papermark](https://www.papermark.com) - Data room and document sharing platform with page-level analytics and granular permissions. ([Source Code](https://github.com/mfts/papermark)) (`AGPL-3.0 core`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Enterprise Resource Planning (ERP)

- [ERPNext](https://erpnext.com) - ERP for manufacturing, distribution, retail, trading, services and education. ([Source Code](https://github.com/frappe/erpnext)) (`GPL-3.0`, `self-host`, `hosted`, `REST`, `UI`)
- [Odoo](https://www.odoo.com) - Suite of business applications spanning ERP, CRM, eCommerce and CMS. ([Source Code](https://github.com/odoo/odoo)) (`LGPL-3.0`, `self-host`, `RPC`, `UI`)

## Commerce

- [Saleor](https://saleor.io) - Headless, GraphQL-first e-commerce platform. ([Source Code](https://github.com/saleor/saleor)) (`BSD-3-Clause`, `self-host`, `GraphQL`, `MCP`, `UI`)

## Project and Work Management

- [monday.com](https://monday.com) - Work platform where people and AI agents manage and run work together. (`hosted`, `GraphQL`, `MCP`, `UI`)
- [Plane](https://plane.so) - Project management with projects and a wiki, for teams and AI agents. ([Source Code](https://github.com/makeplane/plane)) (`AGPL-3.0 core`, `self-host`, `MCP`, `REST`, `UI`)

## Scheduling

- [Cal.com](https://cal.com) - Customizable scheduling software for online bookings. (`hosted`, `REST`, `OpenAPI`, `UI`)

## Data Platforms

- [Appwrite](https://appwrite.io) - Developer platform with authentication, databases, storage, functions, messaging and sites. ([Source Code](https://github.com/appwrite/appwrite)) (`BSD-3-Clause`, `self-host`, `MCP`, `CLI`, `UI`)
- [Baserow](https://baserow.io) - No-code database and application builder. ([Source Code](https://gitlab.com/baserow/baserow)) (`MIT core`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [Busabase](https://busabase.com) - Database and workspace shared by agents and people, where every change keeps its history and important writes can wait for review. (`hosted`, `MCP`, `OpenAPI`, `CLI`, `UI`)
- [Directus](https://directus.com) - Collaborative backend and headless CMS over any database, with a no-code interface. ([Source Code](https://github.com/directus/directus)) (`MSCL-1.0-GPL`, `self-host`, `MCP`, `REST`, `UI`)
- [NocoDB](https://nocodb.com) - No-code platform on top of a database, as an alternative to Airtable. ([Source Code](https://github.com/nocodb/nocodb)) (`Sustainable Use`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [Palantir Foundry Ontology](https://www.palantir.com/docs/foundry/ontology/overview) - Operational layer that sits on top of the data integrated into Palantir Foundry. (`hosted`, `REST`, `CLI`, `UI`)
- [Semantius](https://www.semantius.com) - Data platform on Postgres that enforces business rules, approvals and permissions for every person, app and agent. ([Source Code](https://github.com/semantius/semantius)) (`MIT`, `self-host`, `MCP`, `CLI`, `UI`)
- [Superhuman Docs](https://superhuman.com/docs) - Workspace of docs with tables, formulas and buttons, formerly Coda. (`hosted`, `MCP`, `OpenAPI`, `UI`)

## Communication Systems

- [AgentMail](https://www.agentmail.to) - Email provider that gives AI agents real inboxes over an API. (`hosted`, `REST`, `MCP`, `IMAP`)
- [AgenticMail](https://github.com/agenticmail/agenticmail) - Email, SMS and phone-call infrastructure for AI agents. (`MIT`, `self-host`, `MCP`, `IMAP`, `UI`)
- [Chimely](https://github.com/dodopayments/chimely) - In-app notification inbox with an HTTP API and a drop-in React inbox component. (`AGPL-3.0`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Hook0](https://www.hook0.com) - Webhooks as a service that handles delivery, retries and security for outgoing webhooks. ([Source Code](https://github.com/hook0/hook0)) (`SSPL-1.0`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [Novu](https://novu.co) - Notification infrastructure that reaches users in-app and over email, SMS, push and messaging apps through one API. ([Source Code](https://github.com/novuhq/novu)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Secrets and Access Management

- [authentik](https://goauthentik.io) - Identity provider and single sign-on platform. ([Source Code](https://github.com/goauthentik/authentik)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Infisical](https://infisical.com) - Identity security platform for managing identities, secrets, certificates and access. ([Source Code](https://github.com/Infisical/infisical)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [Keyorix](https://keyorix.com) - Secrets management server with versioned secrets, dynamic credentials and rotation. ([Source Code](https://github.com/keyorixhq/keyorix)) (`AGPL-3.0`, `self-host`, `CLI`, `OpenAPI`, `UI`)

## Workflow Automation

- [Activepieces](https://www.activepieces.com) - Workspace combining AI chat, agents, automation flows and tables with app integrations. ([Source Code](https://github.com/activepieces/activepieces)) (`MIT core`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [FlowFuse](https://flowfuse.com) - Industrial data platform for building, managing, scaling and securing Node-RED solutions. ([Source Code](https://github.com/FlowFuse/flowfuse)) (`Apache-2.0 core`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [n8n](https://n8n.io) - Workflow automation platform that combines visual building with custom code and AI capabilities. ([Source Code](https://github.com/n8n-io/n8n)) (`Sustainable Use`, `self-host`, `REST`, `OpenAPI`, `UI`)

## Monitoring and Incident Response

- [Keep](https://www.keephq.dev) - Alert management and AIOps platform. ([Source Code](https://github.com/keephq/keep)) (`MIT core`, `self-host`, `REST`, `OpenAPI`, `UI`)
- [OpenStatus](https://www.openstatus.dev) - Uptime monitoring and status page platform with incident management. ([Source Code](https://github.com/openstatusHQ/openstatus)) (`AGPL-3.0`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Product Analytics

- [Databuddy](https://www.databuddy.cc) - Cookieless product analytics for visitors, events, funnels and goals. ([Source Code](https://github.com/databuddy-analytics/Databuddy)) (`AGPL-3.0`, `self-host`, `MCP`, `OpenAPI`, `UI`)
- [PostHog](https://posthog.com) - Developer platform for analytics, session replay, feature flags, experiments, error tracking, logs and AI observability. ([Source Code](https://github.com/PostHog/posthog)) (`MIT core`, `hosted`, `MCP`, `OpenAPI`, `UI`)
- [Umami](https://umami.is) - Web and product analytics without cookies. ([Source Code](https://github.com/umami-software/umami)) (`MIT`, `self-host`, `MCP`, `OpenAPI`, `UI`)

## Standards

The discovery and identity surfaces that clauses 6 and 7 refer to: what software publishes about itself so a caller can find it, and how an agent comes to hold its own credentials. Adoption across sixteen origins is measured in [discovery-survey.md](discovery-survey.md).

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
- [The Golden Rules of Agent-First Product Engineering](https://posthog.com/newsletter/agent-first-product-engineering) - Five rules drawn from rebuilding PostHog's agent interface twice, arguing that agents should reach everything a person can and that a product should be exposed at the level agents reason about rather than one endpoint per screen.
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

Entries are checked against each project's own documentation, source or a live response. Facts go stale and mistakes get made. If something here is wrong about your project, open an issue or a pull request with a link to what shows otherwise, and it will be corrected quickly. The same applies to `considered.md` and `agent-only.md`, linked above, where the reasoning for not listing something is written down.
