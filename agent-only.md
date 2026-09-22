# Agent-only systems

Software that meets the machine-interface clauses of the [inclusion criteria](contributing.md) but fails clause 4: the people who would use it have no interface they could realistically reach for.

The test is the audience, not whether a path exists. A database reachable over SQL passes, because SQL clients are what its engineers already use. A CRM reachable only over REST or MCP does not, because the salespeople whose records these are cannot open a REST API, and telling them to have someone build a client first is the same as telling them no.

If something here is wrong about your project, open an issue or a pull request with a link to what shows otherwise and it will be corrected quickly. Software assessed and not listed for other reasons is in [considered.md](considered.md).

They are recorded here rather than in the readme because agent-first is not agent-only. The distinction is the point of the main list, and the clearest way to hold it is to name the software on the other side of it. Being here is a description, not a verdict. For some operators an agent-only system is exactly the right choice, and both entries below say plainly what they are.

- [CRMKit](https://github.com/crmkit/crmkit) - CRM reachable only through its MCP server, described by its authors as headless by design with no interface and no SDK. (`MIT`, `self-host`, `MCP`)
- [Nakatomi](https://github.com/mrdulasolutions/NakatomiCRM) - Headless CRM exposing every primitive as an HTTP endpoint alongside a streamable MCP endpoint, a self-describing schema manifest, an agent card and capability-scoped API keys. Ships no human interface, in its own words "no UI to click". (`MIT`, `self-host`, `MCP`, `REST`)
