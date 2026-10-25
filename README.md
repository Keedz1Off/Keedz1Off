# Stefan | AI Agent Security

<p align="center">
  <img src="assets/ai-agent-security-cyberpunk-cat.png" width="440" alt="Pixel-art cyberpunk cat operating AI agents in a neon city">
</p>

I investigate **AI agents, MCP integrations, and the systems behind their tools**: identity, permissions, shared state, and resource lifecycles.

My background is in **Web3 security**, including bridge architecture, cross-chain authorization, token accounting, and security invariants. My current focus is **AI Agent Security**, using architecture mapping, source review, AI-assisted tooling, and controlled local testing.

## Selected investigations

### Browser Use — navigation policy and trust boundaries

[Case study](https://github.com/Keedz1Off/browser-use-agent-security-case-study) · [Architecture](https://github.com/Keedz1Off/browser-use-agent-security-case-study/blob/main/FLOW.md) · [Evidence](https://github.com/Keedz1Off/browser-use-agent-security-case-study/blob/main/CASE-STUDY.md)

Traced the task → model → tool → event bus → browser flow. In a direct-tool local check, the navigation tool returned a domain-policy error while the owned receiver still recorded the selected HTTP request.

**Outcome:** documented a navigation-guard enforcement mismatch and its source path. Attacker reachability and exploitable security impact remain unconfirmed.

### FastMCP / MCP Python SDK — authorization, OAuth state, and SSE

[Case study](https://github.com/Keedz1Off/fastmcp-auth-state-sse-case-study) · [Architecture](https://github.com/Keedz1Off/fastmcp-auth-state-sse-case-study/blob/main/FLOW.md) · [Upstream fix verification](https://github.com/modelcontextprotocol/python-sdk/pull/3278#issuecomment-6401226641)

Reviewed authentication, OAuth token lifecycle, shared storage, sessions, and transport failures. Independently reproduced a known MCP SDK SSE bug through FastMCP: the server rejected a revoked credential, but the client continued waiting.

**Outcome:** verified the proposed upstream fix against its exact base and head, with release 2.3.0 as a control, across nine local cases. The tested PR head surfaced the error promptly and allowed a subsequent call on the same connection after reauthorization of the same client. This is verification of a known reliability fix; no authorization bypass or application-wide DoS was established.

### LangGraph application — SQLite resource lifecycle

[Case study and local patch](https://github.com/Keedz1Off/learn-with-genai-resource-lifecycle-case-study) · [Upstream bug report](https://github.com/vandenn/learn-with-genai/issues/19)

Investigated **Learn with GenAI**, an application built on LangGraph. Traced the HTTP stream → workflow → SQLite checkpoint saver flow. Ordinary chat requests completed while their SQLite connections and worker threads remained alive.

**Outcome:** reported an application resource-lifecycle bug and prepared a local cleanup patch. The same nine regression tests went from **1 pass / 8 failures before the patch to 9 passes afterward**, covering completion, errors, cancellation, iterator cleanup, and checkpoint resume. The defect belongs to the application; a LangGraph library vulnerability or exploitable service outage was not established. The patch has not been merged upstream.

### AI Agent Security Lab

[Repository](https://github.com/Keedz1Off/ai-agent-security-lab)

A defensive Python lab covering tool permissions, document-level access, HTML text encoding, and action limits. Includes deterministic tests and seeded randomized policy checks with synthetic data.

## Research focus

- Agent-to-tool trust boundaries and application permissions.
- MCP authentication, authorization, and session lifecycle.
- Memory isolation and untrusted content at retrieval and tool boundaries.
- OAuth token storage, concurrency, timeouts, cancellation, and cleanup.
- Invariant-based testing and clear classification of observed failures.

## How I work

Map the architecture → identify boundaries → define invariants → inspect enforcement → test locally → check controls → report evidence and limits.

I use AI throughout research and testing and disclose that assistance in upstream contributions. Each case records the assessed versions, configuration, observations, and remaining proof gaps. I distinguish library defects, application bugs, configuration risks, and confirmed security impact.

## Web3 background

Earlier work examined cross-chain message flows, bridge authorization, and token-accounting invariants:

- [Arbitrum Bridge](https://github.com/Keedz1Off/arbitrum-bridge-flow-local-review)
- [Optimism Bridge](https://github.com/Keedz1Off/optimism-bridge-flow-local-review)
- [Push Chain Gateway](https://github.com/Keedz1Off/push-chain-gateway-flow-local-review)
- [Solidity Audit Agent](https://github.com/Keedz1Off/solidity-audit-agent) — an evidence-gated review workflow with synthetic examples.

## Work with me

Open to **junior AI security roles, internships, and research collaboration** with teams building agents, MCP services, and tool-enabled applications.

[GitHub](https://github.com/Keedz1Off) · [Telegram](https://t.me/ETHkeedz1) · [Email](mailto:keedzyone@gmail.com)
