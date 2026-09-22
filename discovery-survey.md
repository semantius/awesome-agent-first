# Discovery metadata survey

**Run 2026-09-22.** What sixteen origins in and around this list actually publish about themselves, measured rather than claimed.

Clause 6 of the [inclusion criteria](contributing.md) asks whether a system publishes machine-readable discovery metadata. This page is the evidence behind that clause. It is a snapshot: re-run it before citing it.

## Method

For each origin, one unauthenticated `GET` over HTTPS to six well-known paths, following redirects, with a 15-second timeout. A path counts as published only on a final `200`. No content validation beyond the status code, so a `200` here means a document is served at that path, not that it is well-formed or correct.

```sh
curl -s -o /dev/null -L --max-time 15 -w '%{http_code} %{content_type}' "https://$host/$path"
```

Ninety-six requests. Every origin resolved and answered over TLS, and all sixty-four misses were `404`, with no timeouts, no server errors and no failures to resolve.

## Results

| Origin | agent-configuration | oauth-authorization-server | oauth-protected-resource | mcp.json | agent-skills/index.json | llms.txt |
| --- | :-: | :-: | :-: | :-: | :-: | :-: |
| `agentauthprotocol.com` | no | no | no | no | no | yes |
| `agentmail.to` | no | no | no | no | yes | yes |
| `agentsfirst.dev` | no | no | no | no | no | yes |
| `better-auth.com` | no | no | no | no | no | yes |
| `breakcold.com` | no | yes | yes | yes | yes | yes |
| `cloudflare.com` | no | no | no | yes | no | yes |
| `directus.com` | no | no | no | no | no | yes |
| `linear.app` | no | no | no | no | no | yes |
| `neon.com` | no | no | no | no | yes | yes |
| `relaticle.com` | no | yes | yes | no | no | yes |
| `resend.com` | no | yes | yes | yes | yes | yes |
| `semantius.com` | no | no | no | no | no | yes |
| `stripe.com` | no | no | no | no | no | yes |
| `supabase.com` | no | no | no | no | yes | yes |
| `tigerdata.com` | no | no | no | no | no | yes |
| `vercel.com` | no | yes | no | no | yes | yes |

Totals, out of sixteen origins:

| Surface | Published |
| --- | :-: |
| `llms.txt` | 16 |
| `/.well-known/agent-skills/index.json` | 6 |
| `/.well-known/oauth-authorization-server` (RFC 8414) | 4 |
| `/.well-known/oauth-protected-resource` (RFC 9728) | 3 |
| `/.well-known/mcp.json` | 3 |
| `/.well-known/agent-configuration` (Agent Auth) | 0 |

## What this shows

**`llms.txt` is universal in this sample, at sixteen of sixteen.** It is also the cheapest surface on the list: a plain-text file at the site root. That combination makes it close to worthless as a way of telling systems apart, and a reasonable floor to expect of any of them.

**OAuth metadata is what discriminates.** Four origins publish authorization-server metadata and three publish protected-resource metadata, which is the pair that lets a caller find the authorization server and learn the scopes it accepts without being configured in advance. Two of those are CRMs on the shelf this list covers.

**No origin publishes `/.well-known/agent-configuration`.** Nor do the Agent Auth Protocol's own domains. The specification says a server *should* publish the document rather than *must*, so a `404` is not a protocol violation.

## Limits of this measurement

- **It measures public advertisement on the canonical web origin, nothing more.** Discovery documents live at the *authorization server's* origin root, which is often not the marketing domain. A miss on `neon.com` does not rule out a document at some `auth.` or `api.` subdomain.
- **Absence is not proof of non-implementation,** for the same reason, and because several of these surfaces are specified as optional.
- **Self-hosted projects have no canonical origin to probe.** The self-hostable entries in this list are therefore absent from the table rather than scored as missing. Probing a demo instance would measure whoever deployed it.
- **Status codes only.** A `200` was not checked for parseable content or required fields, so a catch-all route that answers everything would be counted as publishing.
