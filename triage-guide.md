# Triage Guide

How I set priority and decide whether to resolve or escalate. One page, used on every ticket.

## 1. Set priority by impact first, then urgency

| Priority | Ask | Examples |
| --- | --- | --- |
| **P1 Highest** | Are **many users** unable to work? | Shared drive offline for a team, no internet for a floor |
| **P2 High** | Is **one user** completely unable to work, or is there a **security risk**? | Locked out, laptop dead, entered password on a phishing page, employee leaving today |
| **P3 Medium** | Can they work, just **slower or with a workaround**? | Slow PC, printer offline, Teams audio, Wi-Fi drops |
| **P4 Low** | Is it a **request or a question**? | Second monitor, software install, "how do I change my password?" |

Rules of thumb:
- **Ask before you rank.** "Is it just you, or others too?" turns a P2 into a P1 more often than anything else.
- **Security beats convenience.** Phishing with entered credentials and same-day offboarding are at least P2, even though nothing looks "broken."
- **Re-triage when facts change.** If a second user reports the same problem, raise the priority and link the tickets.
- **Customers don't set priority.** The agent sets it during triage, so it reflects impact rather than frustration.

## 2. First response

- Reply with **one** clarifying question that changes what you'll do next.
- Verify identity before any password, MFA or access change (callback to the number on file, or the company's process).
- Use **internal notes** for everything technical. Replies to the user stay plain-language.

## 3. Resolve or escalate

**Resolve at tier 1 when** the fix is within help desk permissions and documented: unlocks, resets, group changes with approval, drive maps, DNS settings, trust repair, spooler, browser cleanup, standard hardware swaps.

**Escalate when:**

| Situation | Escalate to |
| --- | --- |
| Credentials entered on a phishing page, malware found, suspicious sign-ins | **Security**, immediately after containment |
| VPN, Wi-Fi coverage, firewall, or anything needing network device access | **Network** |
| Same issue for many users, or tier 1 fix didn't hold | The owning team; open a problem record |
| Needs approval you don't have (spending, access, offboarding without HR) | The **approver**; ticket waits in Pending |
| Privileged or executive accounts | Senior admin per policy |

## 4. Handoff note (every escalation)

> **Reported:** what the user said, in their words
> **Impact:** who and how many; can they work?
> **Checked:** each step and its result
> **Ruled out:** what it isn't
> **Why escalating:** what's beyond tier 1
> **User contact:** best time and method

Escalated tickets stay **open** until the receiving team resolves them. The user gets a reply explaining who has it and what to expect.
