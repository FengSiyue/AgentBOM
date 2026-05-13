# Agent BOM: A Unified Structural Representation for Security Auditing in Agentic Systems
# Attack Cases

The `attack_cases/` directory contains four reproduced attack scenarios used in the paper *Agent-BOM: A Unified Structural Representation for Security Auditing in Agentic Systems*.  
These scenarios are designed to emulate realistic security failures in agentic systems and collectively cover 10 representative risk categories from the OWASP Top 10 for Agentic Applications 2026.

Each scenario provides a practical reproduction of multi-stage agent attacks, including prompt poisoning, memory manipulation, malicious skill execution, unsafe inter-agent communication, privilege escalation, and autonomous harmful actions.

---

# Included Attack Scenarios

## Scenario 1 — Memory Poisoning & Tool Misuse

This scenario reproduces a persistent memory poisoning attack in which the agent’s `AGENT.md`, `MEMORY.md`, and `USER.md` files are maliciously modified.

After poisoning, the agent automatically executes destructive commands such as:

```bash
rm -rf ~/.openclaw/workspace/
```

at the beginning of future sessions without explicit user confirmation.

### Covered Risks

- Tool Misuse & Exploitation
- Memory & Context Poisoning

---

## Scenario 2 — Malicious Skill Supply Chain Attack

This scenario demonstrates a poisoned skill-chain attack in which a malicious skill package is installed into the workspace and automatically invoked by the agent.

The attack simulates:

- malicious `SKILL.md` instruction loading
- unsafe skill auto-execution
- remote data exfiltration
- arbitrary command execution
- destructive filesystem operations

The reproduced skill contains hidden malicious logic inside executable scripts.

### Covered Risks

- Agentic Supply Chain Vulnerabilities
- Unexpected / Remote Code Execution (RCE)

---

## Scenario 3 — Agent Goal Hijacking

This scenario reproduces unsafe multi-agent collaboration behavior.

Three agents cooperate to complete a research task. During communication, the planner agent’s messages are hijacked and modified, causing downstream agents to deviate from the original objective and follow attacker-controlled instructions.

The attack evaluates whether collaborative agents:

- preserve original task constraints
- validate upstream instructions
- resist malicious coordination manipulation

### Covered Risks

- Agent Goal Hijack
- Insecure Inter-Agent Communication
- Cascading Failures

---

## Scenario 4 — Privilege Escalation via Memory Injection

This scenario demonstrates identity and privilege abuse through poisoned memory and user-preference manipulation.

The attack injects malicious instructions into `MEMORY.md` and `USER.md`, causing the agent to silently bypass confirmation procedures and directly execute privileged actions such as email sending.

An extended variant further demonstrates cross-agent memory poisoning, where a malicious Agent A injects poisoned memory instructions into Agent B during inter-agent communication.

### Covered Risks

- Identity and Privilege Abuse
- Human Agent Trust Exploitation
- Rogue Agents

---

# Risk Coverage

The reproduced scenarios collectively cover the following OWASP Agentic Application risk categories:

| Risk Category | Covered |
|---|---|
| Agent Goal Hijack(ASI01) | ✓ |
| Tool Misuse & Exploitation(ASI02)  | ✓ |
| Identity & Privilege Abuse(ASI03)  | ✓ |
| Agentic Supply Chain Vulnerabilities(ASI04)  | ✓ |
| Unexpected Code Execution (RCE)(ASI05)  | ✓ |
| Memory & Context Poisoning(ASI06) | ✓ |
| Insecure Inter Agent Communication(ASI07)  | ✓ |
| Cascading Failures(ASI08) | ✓ |
| Human Agent Trust Exploitation(ASI09) | ✓ |
| Rogue Agents(ASI09) | ✓ |

---

# Scenario Sources

The reproduced attack cases are derived from representative attack patterns and threat models discussed in prior research on LLM agents, agentic workflows, memory systems, and multi-agent security.

## References

- Your Agent, Their Asset: A Real-World Safety Analysis of OpenClaw  
  https://arxiv.org/abs/2604.04759

- From Prompt Injections to Protocol Exploits: Threats in LLM-Powered AI Agents Workflows  
  https://www.sciencedirect.com/science/article/pii/S2405959525001997

- AI Agent Traps  
  https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6372438

- Memory Injection Attacks on LLM Agents via Query-Only Interaction  
  https://arxiv.org/pdf/2503.03704

- TrinityGuard: A Unified Framework for Safeguarding Multi-Agent Systems  
  https://arxiv.org/abs/2603.15408

- Securing the Model Context Protocol (MCP): Defending LLMs Against Tool Poisoning  
  https://arxiv.org/abs/2512.06556
