# Contribution Guidelines

Thanks for suggesting an entry. This project is released with a [Contributor Code of Conduct](code_of_conduct.md); by participating you agree to abide by its terms.

Two separate gates decide whether software is listed. Meeting the definition makes a project *eligible*. It is *listed* only if it also clears the quality bar.

Everything assessed and not listed is written down in [considered.md](considered.md), with the clause it failed and what would change that, so before suggesting something check whether it is already there. If it is and the situation has changed, open an issue saying what changed and it gets re-checked. Software that fails clause 4 by design is in [agent-only.md](agent-only.md) instead.

The gates apply to the software sections. The readme's last two sections, Standards and Assessment and Reading, are reference material: the specifications the clauses refer to, and the rubrics and writing worth reading. Suggest an addition there if it is normative, widely implemented, or genuinely useful for evaluating software against the clauses. Those entries carry no tags, because tags describe a listed project.

## Gate one: the definition

**Agent-first software** is built to be used by autonomous agents and by people alike. It is a producer: it exposes capability, and an agent consumes it. The software gains no agency of its own.

All four of these must hold.

1. **The software is the product, not the agent.** It provides a capability an agent puts to use, whether that is holding records, running a workflow, managing infrastructure or sending messages. Agents, and the frameworks used to build them, sit on the other side of that line.
2. **The machine interface is primary, not additive.** An API, CLI or MCP server reaches the same capabilities as any human interface, and the documentation is written for a machine caller. A chat window bolted onto an existing product does not qualify, and neither does an API covering a subset of what the interface can do.
3. **The model describes itself at runtime.** Entities, fields and operations carry names and descriptions a caller can read from the software itself, whether by generated schema, introspection or published metadata, so a caller needs no out-of-band instructions. Filtering is granular, and there is full-text or vector search over the model rather than one fixed endpoint per screen.
4. **People keep a path to the same capability, in tools the software's own users would actually reach for.** A shipped interface counts. So does an open protocol, but only where a general-purpose client already exists for those particular users: SQL clients for a database whose users are engineers, IMAP for a mailbox. Judge the path against the audience, not against whether a path exists at all. A CRM reachable only over SQL fails, because salespeople do not manage records in a database client, even though that same path is enough for a database whose users are engineers. A REST or MCP API never satisfies this on its own, because reaching your own data should not require building a client first.

And at least one of these.

5. **Authorization is enforced by the system,** not re-implemented by every caller.
6. **The software publishes machine-readable discovery metadata:** OpenAPI, OAuth authorization-server or protected-resource metadata, an MCP server card, `llms.txt`, or an agent-skills index.
7. **Agents can hold their own credentials,** scoped and revocable independently of a person's session.

## Verifying clauses 2 and 3

Clauses 2 and 3 are settled by running the software, not by reading what it says about itself. The test is a round trip an agent completes with no person writing integration code.

**Configure.** Starting from a fresh instance, the agent changes the model itself: create an entity or collection, add fields of more than one type, create a role, and grant that role a permission narrower than full access.

What this half measures is parity with the human interface, not absolute power. Software with a fixed model that nobody can extend at runtime passes it vacuously, because both interfaces reach equally far, and that is fine. The failure it exists to catch is software whose admin interface can define fields, roles or object types that its own API cannot, which is clause 2's "an API covering a subset of what the interface can do". Report which of the two situations you found, because "the agent could not add a field" means nothing on its own.

**Operate.** Using only what it just configured, the agent creates a record, finds it by something other than its identifier, updates it, deletes it, and is correctly refused an operation the narrowed role does not allow.

Chaining the two halves is the point. Configuration is what separates software built to be operated by an agent from software with an API bolted onto a subset of an admin interface, and operating against a model the agent defined itself is what proves the model is readable at runtime.

Throughout, the agent may read the software's own documentation, schema and metadata, and nothing else. It may not be handed instructions written for that specific product, a pre-built client library, or browser automation driving a human interface. Without those limits the test grades the agent rather than the software, because a capable agent can drive almost anything.

**Clause 4 is checked separately,** and the round trip is blind to it. Confirm that a person can reach the same configuration and the same records through a shipped interface or an open protocol. Software that passes the round trip and fails this is agent-only, and belongs in [agent-only.md](agent-only.md). Agent-first means the admin interface is not needed, not that it is absent.

Record the date, the agent and the model used. Results move as models improve, so an undated result is not evidence.

## Gate two: the quality bar

- It has a licence.
- Its documentation is public and good enough to evaluate without signing up.
- It has had a commit in the last six months.
- It is not archived or deprecated.

## Not on this list

- **Agent frameworks, orchestrators and SDKs.** They build the consumer, not the producer.
- **Agents themselves,** and agent app stores or skill catalogs.
- **Agent runtime infrastructure** such as sandboxes, browsers, search APIs, memory stores, model gateways and observability is largely covered by the lists in the readme's Related Lists section. It is in scope here only when it meets all four clauses, and a suggestion should say why those lists do not already serve it.
- **Connectors over someone else's system.** An MCP server in front of a product is a connector; what gets assessed is the product underneath.
- **Products whose agent support was added afterwards** and covers only part of the product.
- **Agent-only systems** that leave people no path to their own data. Those go in [agent-only.md](agent-only.md).
- **General-purpose databases and warehouses.** Administering a database over SQL and an API is ordinary rather than agent-first, and is equally true of Snowflake, Databricks, Redshift, ClickHouse and PostgreSQL itself. A data platform is listed only when it ships capability built for agents specifically: cheap isolated forks for an agent to work against, retrieval designed for filling agent context, or a first-party MCP server governed by the same permissions as everything else.
- **Systems whose model is configured only through a UI.** If object types, fields, roles or permissions can be created only by clicking, the software fails clause 2 no matter how good the query API is. A CLI is an interface an agent can call, so the test is not whether the definition lives in a file. It is whether the running software reconfigures itself when it is handed one. Software that reaches its new model through a command the vendor ships and the agent runs itself passes. Software whose model is part of its own source, so that changing it means rebuilding and redeploying the application, does not.

## Opening a pull request

- Work on a branch, not on `main`.
- Say which category the entry belongs in, and open an issue first if you think a new category is needed.
- Say, in the pull request body, how the entry meets each of clauses 1 to 4 and which of 5 to 7 it meets. Cite the project's own documentation, SDK source or a live response, not a summary or a search result.
- Run the round trip above and report what happened: the agent and model you used, the date, what you configured, and where it needed help. A run that failed somewhere is still useful, and saying so is better than omitting it.
- Add the entry in alphabetical order within its section.
- If it duplicates an existing entry, say why it should replace that one.
- Check spelling and grammar, and run `npx awesome-lint` before opening the pull request.

## Entry format

One line, a dash separator, an objective description that starts with a capital and ends with a period, no hard wrapping, and at most five tokens.

```
- [Name](https://example.com) - Objective description of what it is. ([Source Code](https://github.com/x/y)) `MIT` `self-host` `MCP` `CLI` `UI`
```

Describe the project, not this list. "Mobile operating system for Apple phones and tablets", not "Resources and tools for iOS development". Vendor taglines get rewritten.
