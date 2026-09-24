# Contribution Guidelines

Thanks for suggesting an entry. This project is released with a [Contributor Code of Conduct](code_of_conduct.md); by participating you agree to abide by its terms.

Two separate gates decide whether software is listed. Meeting the definition makes a project *eligible*. It is *listed* only if it also clears the quality bar.

Everything assessed and not listed is written down in [considered.md](considered.md), with the clause it failed and what would change that, so before suggesting something check whether it is already there. If it is and the situation has changed, open an issue saying what changed and it gets re-checked. Software that fails clause 4 by design is in [agent-only.md](agent-only.md) instead.

The gates apply to the software sections. The readme's last two sections, Standards and Assessment and Reading, are reference material: the specifications the clauses refer to, and the rubrics and writing worth reading. Suggest an addition there if it is normative, widely implemented, or genuinely useful for evaluating software against the clauses. Those entries carry no tags, because tags describe a listed project.

## Gate one: the definition

**Agent-first software** is built to be used by autonomous agents and by people alike. It is a producer: it exposes capability, and an agent consumes it. The software gains no agency of its own.

All four of these must hold.

1. **The software is the product, not the agent.** It provides a capability an agent puts to use, whether that is holding records, running a workflow, managing infrastructure or sending messages. Agents, and the frameworks used to build them, sit on the other side of that line.
2. **An operator can run the software with only an agent.** Everything needed to configure and operate it is reachable through an API, CLI or MCP server, and the documentation is written for a machine caller. That means defining the model, granting access to it, and working with the records, in whatever vocabulary the software uses for those things. The admin interface is not needed. A chat window bolted onto an existing product does not qualify, and neither does a machine interface that stops short of what an operator has to do.

    The test is what an operator needs, not every affordance the interface offers. Presentation settings, themes and onboarding tours are not in scope. Defining entities and fields, granting access, and creating, finding, updating and deleting records are.

    Assessed against an agent with shell and filesystem access that can run repository workflows, which is the capability class of the coding agents in general use. A path that requires running a command the vendor ships, editing a configuration file or deploying a repository counts, because such an agent does those things. A path that requires a person to click does not.
3. **The model describes itself at runtime.** Entities, fields and operations carry names and descriptions a caller can read from the software itself, whether by generated schema, introspection or published metadata, so a caller needs no out-of-band instructions. Filtering is granular, and there is full-text or vector search over the model rather than one fixed endpoint per screen.
4. **People keep a path to the same capability, in tools the software's own users would actually reach for.** A shipped interface counts. So does an open protocol, but only where a general-purpose client already exists for those particular users: SQL clients for a database whose users are engineers, IMAP for a mailbox. Judge the path against the audience, not against whether a path exists at all. A CRM reachable only over SQL fails, because salespeople do not manage records in a database client, even though that same path is enough for a database whose users are engineers. A REST or MCP API never satisfies this on its own, because reaching your own data should not require building a client first.

And at least one of these.

5. **Authorization is enforced by the system,** not re-implemented by every caller.
6. **The software publishes machine-readable discovery metadata:** OpenAPI, OAuth authorization-server or protected-resource metadata, an MCP server card, `llms.txt`, or an agent-skills index.
7. **Agents can hold their own credentials,** scoped and revocable independently of a person's session, and act as a participant wherever the software has one (an assignee, a reviewer, a watcher), so that what the software records about who did what names the agent.

## Verifying clauses 2 and 3

Clauses 2 and 3 are settled from what the software publishes about itself: its reference documentation, its generated schema, and the metadata it serves at runtime. That is the same material an agent has, and an agent reduced to discovering capability by trial and error has already been failed by clause 3, which asks that a caller need no out-of-band instructions. So an assessment reads what a caller would read, and an entry cites it.

A finding is worth what the documentation under it is worth. Concluding that an API cannot do something is an argument from silence, and silence carries weight in a reference that indexes every endpoint while proving little in a thin one. Thin documentation is itself a clause 3 finding rather than an excuse for an inconclusive one.

Capability the reference never mentions but the running system exposes still counts, because clause 3 accepts a generated schema, introspection or published metadata as self-description, and a caller that can find it can use it. Cite the schema or the introspection result there, the same way you would cite a documentation page.

**The round trip below is the preferred evidence for clause 2.** An operator test is a question about what happens when you run the software, and running it answers that better than reading about it does, without the argument from silence above. A finding settled from documentation alone remains acceptable where the reference is thorough, and is the only option for software nobody outside the vendor can obtain. Run the round trip in particular where the documentation is thin or contradicts itself, where something is documented but reported not to work, or where a vendor disputes a finding.

Clause 3 stays a reading test, because what it asks is whether a caller can discover capability without out-of-band instructions, and that is answered by what the software publishes rather than by what a determined agent eventually got working.

**Configure the model.** Starting from a fresh instance, the agent changes the model itself: create an entity or collection, and add fields of more than one type.

**Configure access to it.** The agent then grants access to what it has just built, narrower than full, through whatever grouping the software actually has: a role, a group, a team, or a permission level on that one resource. Where the software defines its own roles, the agent defines one and grants through it. Where the roles are a fixed set, assigning an existing one is the whole of the test.

The access model has two planes, and only one of them is the software's to answer for. Who exists, and which groups they belong to, is the identity plane, and in an enterprise deployment that belongs to the identity provider and arrives over SCIM. Software that delegates it is not falling short of anything, and SCIM is a machine interface like any other, describing itself through `/Schemas` and `/ResourceTypes`. What a role permits in the software's own vocabulary, and which resources it reaches, is the authorization plane. No identity provider can hold that, because "may edit the Deals table but not delete records" is vocabulary that exists only inside the application, and SCIM's own `roles` and `entitlements` attributes carry a role's name onto a user without saying anything about what it permits. The authorization plane is what this half tests.

What the configure half measures is what an operator needs, not absolute power. Software with a fixed model that nobody can extend at runtime still passes, because an operator needs no admin interface to run it, and software that has genuinely handed a plane to an identity provider passes for the same reason. What fails is an asymmetry inside one product: something an operator must do that only the interface can reach, such as an admin interface that defines fields, roles or object types its own API cannot. Report which of these you found, because "the agent could not add a field" means nothing on its own.

Weigh the per-resource grant above the role definition. Scoping a table it has just built to one team is what an agent does constantly, while minting a named role with a custom permission bundle is a quarterly administrative act. Software that reaches every per-resource grant and falls short only at defining a new role has a narrow gap, and the write-up should say so in those words rather than reporting a blanket failure.

**A refusal is not a gap.** A capability the machine interface refuses on authorization grounds is the access model working, and clause 5 is the reason: a differently scoped credential succeeds, and the refusal is the one a person would meet too. A capability with no machine-callable form fails clause 2 whatever reason is given for it, because the most privileged credential the software issues meets the same wall as the least. Tell the two apart by attempting the operation with that most privileged credential. Where a vendor documents a deliberate reason for withholding something, quote it, and say that the remedy is a scope rather than an endpoint.

**A bootstrap step is not a gap.** Some software has a one-time setup action that unlocks the rest of its machine interface and then never recurs: enabling multi-user mode, creating the first administrator, issuing the first key. That is installation rather than a gap, so "a fresh instance" above means one that has finished its own setup, and the round trip starts there. The question to ask is whether an agent would hit the same step again next week. If not, it is installation. What fails clause 2 is an asymmetry that survives setup, such as a schema builder that stays read-only in production however the instance was installed, because no state exists in which the API reaches what the interface reaches. Where the bootstrap step itself has no machine-callable form, record it as a clause 3 finding about discovery, and say whether a caller could have found it in the published schema.

**Operate.** Using only what it just configured, the agent creates a record, finds it by something other than its identifier, updates it, deletes it, and is correctly refused an operation the narrowed grant does not allow.

Chaining configuration and operation is the point. Configuration is what separates software built to be operated by an agent from software with an API bolted onto a subset of an admin interface, and operating against a model the agent defined itself is what proves the model is readable at runtime.

Throughout, the agent may read the software's own documentation, schema and metadata, and nothing else. It may not be handed instructions written for that specific product, a pre-built client library, or browser automation driving a human interface. Without those limits the test grades the agent rather than the software, because a capable agent can drive almost anything.

**Clause 4 is checked separately,** and the round trip is blind to it. Confirm that a person can reach the same configuration and the same records through a shipped interface or an open protocol. Software that passes the round trip and fails this is agent-only, and belongs in [agent-only.md](agent-only.md). Agent-first means the admin interface is not needed, not that it is absent.

Record what you read, and link it. If you ran the round trip live, record the agent and the model as well, since results move as models improve. An entry that names no agent was settled by reading, so there is nothing to label on the entries that were.

## Gate two: the quality bar

- It has a licence. For open-source software that means a licence file in the repository, because code published without one is all rights reserved and nobody may use it. Commercial software is covered by the terms it is sold under, and is not expected to carry one.
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
- **Single-device software.** Software that runs for one person on one machine has no access model to grant through, because no second person or agent can reach the same data under access of their own. Local-first software is eligible only where it also serves or syncs a shared workspace, and that shared edition is what gets assessed.
- **General-purpose databases and warehouses.** Administering a database over SQL and an API is ordinary rather than agent-first, and is equally true of Snowflake, Databricks, Redshift, ClickHouse and PostgreSQL itself. A data platform is listed only when it ships capability built for agents specifically: cheap isolated forks for an agent to work against, retrieval designed for filling agent context, or a first-party MCP server governed by the same permissions as everything else.
- **Systems whose model is configured only through a UI.** If object types, fields, roles or permissions can be created only by clicking, the software fails clause 2 no matter how good the query API is. A CLI is an interface an agent can call, so the test is not whether the definition lives in a file, nor whether reaching the new model takes a deploy. It is whether the running software reconfigures itself when an agent hands it one, unaided. Software that reaches its new model through a command the vendor ships, a configuration file the agent edits or a repository workflow the agent runs passes, because an agent with a shell does all three. What fails is a step only a person can take.

## Opening a pull request

- Work on a branch, not on `main`.
- Say which category the entry belongs in, and open an issue first if you think a new category is needed.
- Say, in the pull request body, how the entry meets each of clauses 1 to 4 and which of 5 to 7 it meets. Cite the project's own documentation, SDK source or a live response, not a summary or a search result.
- Work the clauses from what the software publishes, and link the page, the schema or the metadata behind each one. Where reading did not settle it and you ran the round trip above, report what happened: the agent and model you used, what you configured, and where it needed help. A run that failed somewhere is still useful, and saying so is better than omitting it.
- Add the entry in alphabetical order within its section.
- If it duplicates an existing entry, say why it should replace that one.
- Check spelling and grammar, and run `npx awesome-lint` before opening the pull request.

## Entry format

One line, a dash separator, an objective description that starts with a capital and ends with a period, no hard wrapping, and at most five tokens.

```
- [Name](https://example.com) - Objective description of what it is. ([Source Code](https://github.com/x/y)) (`MIT`, `self-host`, `MCP`, `CLI`, `UI`)
```

Describe the project, not this list. "Mobile operating system for Apple phones and tablets", not "Resources and tools for iOS development". Vendor taglines get rewritten. Leave out counts, such as the number of tools, endpoints or paths, because they go stale.
