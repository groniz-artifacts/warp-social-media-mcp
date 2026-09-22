# How to Connect Warp to Social Media With MCP

Connect Warp to social media by adding Groniz through Warp's current MCP server setup under Settings → Agents → MCP servers. Use `https://mcp.groniz.com/mcp`. Check the current [Warp documentation](https://docs.warp.dev/) and [MCP server reference](https://docs.warp.dev/reference/cli/mcp-servers) while configuring it. The older `oz` binary is being deprecated in favor of `warp`, so old `oz` commands should not be the preferred setup path.

Give Warp an approved post or media packet. The connector can be available to local and cloud agents, but a person must still review the facts, rights, disclosures, destination, final payload, and time before the write. Upload media first and submit once. Capture the returned post ID, and reconcile an uncertain response before retrying.

## Freeze the asset before choosing an agent

Warp's agents can move between terminal work and cloud execution, but the content boundary should stay stable. Name the approved source and version before any agent prepares a public payload.

```markdown
Canonical source asset:
Approved version:
Owner:
Facts and links verified by:
Rights and consent verified by:
Disclosure decision:
Approved copy or adaptation limits:
Approved media:
Allowed destination and timing window:
```

Research, creation, recording, editing, approval, and rights or disclosure checks for this packet stay outside Groniz. The acting Warp agent may assemble a delivery proposal, but the account operator retains those decisions and approves the final destination-specific payload.

If the source begins as a product update for community channels, the [OpenClaw Discord and Telegram workflow](https://groniz.com/blog/openclaw-product-updates-discord-telegram) demonstrates why one factual source can still require separate destination decisions. Warp uses a different client path, but the source-control principle carries over.

## Use Warp’s current MCP path

Begin from the current documentation and the current product settings route: Settings → Agents → MCP servers. Add the remote Groniz endpoint:

```text
https://mcp.groniz.com/mcp
```

Warp shares MCP server access across its local and cloud agents. One reviewed server definition can therefore work in more than one execution context. The acting context still belongs in the setup record. Write down whether the first delivery will run locally or in a cloud agent, which identity is connected, and where authentication is available.

Do not treat a server that appears in both contexts as proof that both have the same file access, credentials, or task history. Test the exact agent that will perform the real delivery. Confirm it reaches the intended endpoint and can discover the expected tools before exposing a social write.

For a comparison with other clients’ configuration boundaries, use the [client-by-client social publishing setup](https://groniz.com/blog/ai-agent-social-media-publishing-setup). The [social media MCP server guide](https://groniz.com/blog/social-media-mcp-servers) explains the difference between reaching a tool and validating the publishing system behind it.

## Detect stale `oz` instructions

Older Warp MCP material may use the `oz` binary. Warp is deprecating that binary in favor of `warp`, so do not silently copy an `oz` command into a current runbook or present it as the preferred route.

Use this original setup asset to check the current path and catch deprecated commands:

| Check | Acceptable evidence | Stop condition |
| --- | --- | --- |
| Documentation | Current Warp docs and current MCP reference | An undated snippet or third-party post is the only source |
| Settings path | Settings → Agents → MCP servers or the current documented equivalent | The instructions depend on a screen that cannot be found in current docs |
| CLI name | Current `warp` guidance where a CLI step is needed | The procedure requires an old `oz` command as its preferred path |
| Execution context | Local or cloud agent named explicitly | The operator cannot tell which agent will invoke the write |
| Authentication | Tested in that execution context | A credential exists only in another context |
| Approval | Final social write remains reviewable | Server availability is treated as permanent publishing permission |

If current documentation changes the navigation or supported command shape, update the runbook to match it. Keep the durable parts in view: the remote endpoint, authentication, live tool discovery, and approval boundary. Do not claim an unobserved current UI beyond the documented path.

## Authenticate for the actual execution context

Groniz remote MCP supports OAuth 2.0, an `Authorization: Bearer YOUR_API_KEY` header, or a key embedded in the endpoint URL. Prefer OAuth when the current Warp MCP path can complete it for the agent that will publish.

If the environment requires a key, use Warp’s current protected credential mechanism and test it in the same local or cloud context. The issuance location is [Groniz Connectors API keys](https://groniz.com/console/connectors/api-keys). Never copy a real value into a terminal prompt that will be saved, a shared settings screenshot, a repository, or a delivery log. Treat a key-bearing URL as a secret as well.

Authentication proves that the chosen Warp agent can reach Groniz. It does not prove that the intended social account is connected, the destination settings are satisfied, or the post is approved.

Before enabling a write, check the connection in the chosen context. Record the Warp version, documentation page consulted, local or cloud context, visible server name, endpoint without any credential, and test time. Confirm that the agent can enumerate the live tools and perform the required read operations. If the runbook includes a command from an older setup, compare it with the current reference and replace it with the documented `warp` route. The next operator can then distinguish a working configuration from a stale snippet that merely looks plausible.

## Discover the destination before preparing the payload

Ask the acting agent to begin with read-only inspection:

```text
discover the live MCP tools
→ list connected integrations
→ resolve the exact account, Page, community, or channel
→ inspect its current required settings
→ prepare one destination-specific payload
```

Include both a stable integration reference and a human-readable account label in the run record. "Use the main channel" is too vague when several similarly named destinations exist. If the evidence cannot distinguish them, ask an operator to choose.

Groniz handles provider OAuth, per-platform formatting, and delivery to 32+ networks, but providers do not expose identical fields, media, analytics, or scheduling. The live integration settings are authoritative. Do not hardcode provider-specific Groniz fields from an example or carry one destination’s options into another.

Upload approved media before posting. Confirm that the supported upload completed and bind the returned media reference to the intended destination packet. The reviewer needs to see the attachment order and any destination settings that affect how the post will appear.

## Keep the local or cloud write behind one review

Before submission, the agent should display this complete proposal without credentials:

```markdown
Acting Warp context: local / cloud
Source asset and version:
Network and exact connected account:
Final text, links, and disclosure:
Uploaded media references and order:
Live destination settings:
Publish now or schedule:
Local time and named timezone:
Exact timestamp with offset:
Write operation:
```

The person approving it verifies the facts, rights, disclosure, destination, payload, media, and time together. If the agent changes any item afterward, cancel the write and return to review. A server shared across agents is infrastructure, not blanket approval for them to publish.

Record the reviewer and a stable approval reference in the run. This helps distinguish a delivery the operator actually approved from an action that merely came from a configured agent.

## Submit once, then verify or recover

Invoke the approved write once. Capture the submission timestamp, acting context, integration, approved payload version, response state, and returned post or scheduled-record ID.

For an immediate post, inspect the supported delivery state and the public destination when a public reference is available. For a schedule, check that the stored account, content, time, timezone, and offset match the approved packet. Acceptance or a schedule record is useful evidence, but neither should be mislabeled as a verified public result.

If the local or cloud agent loses the response, keep the outcome unknown. Search the available records and intended destination for the original delivery. Do not switch contexts and resend simply because the first agent has no visible confirmation. Follow the [failed-post reconciliation workflow](https://groniz.com/blog/recover-failed-social-media-posts), rule out a duplicate, correct the cause, and re-approve any material change before one safe retry.

Keep the connection test and delivery evidence together. They document the route, but they cannot establish future reach, engagement, leads, sales, or revenue.

Once the approved source packet and current-path check are complete, [connect Warp’s reviewed delivery route through Groniz Connectors](https://groniz.com/console/connectors).
