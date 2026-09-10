# MCP Threat, Abuse, and Trust-Boundary Matrix

Use this matrix before exposing a consequential capability through MCP. Test
the protocol path and the underlying API path; a secure transport does not
prove a safe business operation.

| Threat or abuse | What the attacker or failure exploits | Boundary that must hold | Test/mutation | Evidence and owner | Status |
| --- | --- | --- | --- | --- | --- |
| Malicious or compromised server | A server returns hostile instructions or data | Only approved servers and versions are discoverable | Replace server metadata or package in a test host | | |
| Tool poisoning | A description encourages unsafe scope or hidden side effects | Descriptions are reviewed and never treated as authority | Alter description without changing schema | | |
| Prompt injection through a resource | Untrusted content changes agent behavior | Resource data cannot grant permission or alter policy | Insert adversarial resource content | | |
| Confused deputy | Server credential acts more broadly than caller | Original principal, tenant, purpose, and delegation survive every hop | Call with mismatched or missing identity | | |
| Credential passthrough | Tokens or secrets become model-visible | Secrets stay in approved execution boundaries | Inspect prompts, tool results, logs, and traces | | |
| Cross-tenant disclosure | A read surface ignores tenant scope | Every read and mutation checks tenant and subject | Request another tenant’s identifier | | |
| Excessive permission | A narrow user need reaches broad admin access | MCP surface is narrower than technical access | Attempt an out-of-scope operation | | |
| SSRF or arbitrary egress | Generic proxy reaches internal destinations | Destinations and protocols are allow-listed | Supply private, metadata, or unexpected URL | | |
| Supply-chain compromise | SDK, package, image, or connector changes behavior | Dependencies are pinned, scanned, reviewed, and reversible | Test a changed dependency/version | | |
| Replay and duplicate effects | Retry or repeated tool call repeats mutation | Business identity and idempotency control distinct effects | Replay, concurrent call, timeout-after-effect | | |
| Resource exhaustion | Discovery, polling, or retries amplify cost | Rate, quota, concurrency, task TTL, and budgets are explicit | Burst requests and dependency slowdown | | |
| Hidden cross-server call | One server invokes another outside policy | Composition path and authority are visible | Remove or alter downstream server permission | | |
| Task result exposure | Guessable task ID reveals another result | Task state is authorization-bound and expires | Cross-principal task retrieval | | |

## Release decision

**Highest-consequence unresolved threat:**  
**Required mitigation or explicit acceptance:**  
**Who may approve residual risk:**  
**Disablement and recovery trigger:**  
**Next review date:**  

Do not mark a threat `pass` because a request was rejected once. Preserve the
test identity, setup, mutation, observed result, and what the test did not
cover.
