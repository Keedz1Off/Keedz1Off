# Stefan | AI Agent Security

![AI agent security — pixel-art sakura banner](assets/ai-agent-security-sakura-banner.png)

I research the security of **AI agents, MCP integrations, and the systems behind their tools**: who can trigger an action, what data it can reach, and whether the intended boundary is actually enforced.

I started in **Web3 security**, reviewing bridge architecture, cross-chain authentication, token accounting, and security invariants. I am now actively focused on **AI Agent Security**, applying the same flow-by-flow approach to agent permissions, authorization, sessions, and shared state.

My work combines source-level analysis, AI-assisted research, and controlled local testing. Below are the investigations, evidence, and technical explanations behind my portfolio.

## Selected investigations

### Browser Use — navigation and trust boundaries

[Repository and report](https://github.com/Keedz1Off/browser-use-agent-security-case-study) · [Architecture](https://github.com/Keedz1Off/browser-use-agent-security-case-study/blob/main/FLOW.md) · [Results](https://github.com/Keedz1Off/browser-use-agent-security-case-study/blob/main/CASE-STUDY.md)

Mapped the task → model → tool → event bus → browser flow. In a direct-tool local check, the receiver recorded an HTTP request even though the navigation tool returned a domain-policy error. I documented the enforcement mismatch, examined the relevant source path, and separated it from unrelated answer-format failures.

**Result:** an evidenced navigation-guard defect. An untrusted-input attack chain and exploitable security impact were not established.

### FastMCP — authorization, OAuth state, and SSE

[Repository and report](https://github.com/Keedz1Off/fastmcp-auth-state-sse-case-study) · [Architecture](https://github.com/Keedz1Off/fastmcp-auth-state-sse-case-study/blob/main/FLOW.md) · [Results](https://github.com/Keedz1Off/fastmcp-auth-state-sse-case-study/blob/main/RESULTS.md)

Reviewed authentication, OAuth token lifecycle, shared storage, session behavior, and transport failures. In the owned SSE stand, the server correctly rejected a revoked test credential, but the waiting client RPC did not promptly surface that rejection. Explicit deadlines bounded the wait; independent work continued during the control test.

**Result:** an evidenced client/dependency error-propagation defect, with additional shared-state and deployment observations. The evidence does not establish an authorization bypass or application-wide DoS.

### AI Agent Security Lab

[Repository](https://github.com/Keedz1Off/ai-agent-security-lab)

A defensive Python lab covering tool permissions, document-level access, HTML text encoding, and action limits. Includes deterministic tests and seeded randomized policy checks, alongside OWASP-mapped learning examples. Uses synthetic data without a live LLM or external services.

## Current research focus

- Agent-to-tool trust boundaries and application-enforced permissions.
- MCP authentication, authorization, and session lifecycle.
- Untrusted content and prompt-injection risks at tool boundaries.
- OAuth token storage, concurrency, timeouts, and cancellation.
- Invariant-based testing and evidence-backed result classification.

## How I work

I trace the architecture and data flow, identify trust boundaries, define invariants, inspect their enforcement in code, and compare expected behavior with local evidence. Reports retain version pins, controls, observed results, and the remaining questions about impact.

I use AI to assist research and testing, while keeping claims tied to source and measurements. These are independent, scoped portfolio studies—not vendor-endorsed production audits. A reproducible bug is not automatically a security vulnerability.

## Web3 background

Earlier work focused on cross-chain message flows, bridge authorization, and token-accounting invariants:

- [Arbitrum Bridge](https://github.com/Keedz1Off/arbitrum-bridge-flow-local-review)
- [Optimism Bridge](https://github.com/Keedz1Off/optimism-bridge-flow-local-review)
- [Push Chain Gateway](https://github.com/Keedz1Off/push-chain-gateway-flow-local-review)
- [Solidity Audit Agent](https://github.com/Keedz1Off/solidity-audit-agent) — an evidence-gated review workflow with synthetic examples.

## Work with me

Open to **junior AI security roles, internships, and research collaboration**, especially with teams building agents, MCP services, and tool-enabled applications.

- GitHub: [Keedz1Off](https://github.com/Keedz1Off)
- Telegram: [@ETHkeedz1](https://t.me/ETHkeedz1)
- Email: [keedzyone@gmail.com](mailto:keedzyone@gmail.com)
