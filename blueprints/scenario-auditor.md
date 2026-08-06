# Lease tool that splits contract lines into separate duties

## Purpose

A conversational auditor that walks five checks against any lease-line splitting tool. The auditor evaluates whether the tool correctly separates conditional clauses (especially "provided that" constructions) so each duty lands on its own line with the right party named.

## What this auditor catches

When a lease tool merges two duties on lines with "provided that," the wrong party looks responsible. A partner signs a summary that puts repair duty on the wrong side.

## Standard for passing

Each duty lands on its own line with the right party named.

---

## The five checks

| Check | What it tests | Score (0–4) |
|-------|---------------|-------------|
| **Unowned** | Is there a named owner for each check? | 1 |
| **Copies** | Does the tool preserve the original text faithfully? | 1 |
| **Room** | Is there space for edge cases and exceptions? | 2 |
| **Stitch** | Does the tool correctly split conditional clauses? | 4 |
| **Ablation** | What breaks if you remove a component? | 0 |

**Top crack:** Stitch — the tool fails to split "provided that" clauses, fusing two duties into one line.

---

## Worked example: Harbor Lease sample contracts

These failing inputs come from old scanned leases with nested "provided that" lines:

**Input 1:**
> Tenant shall repair the roof provided that Landlord funds materials within 10 days.

**Expected output:** Two separate duties:
1. Tenant shall repair the roof
2. Landlord funds materials within 10 days

**Failure mode:** Tool outputs one fused line, making Tenant appear responsible for both.

**Input 2:**
> Fees accrue daily; provided, however, that the cap in §4.2 still applies.

**Expected output:** Two separate duties:
1. Fees accrue daily
2. The cap in §4.2 still applies

**Failure mode:** Tool merges into single line, obscuring the cap condition.

**Input 3:**
> Notice is deemed given when posted, unless the parties agree otherwise in writing.

**Expected output:** Two separate duties:
1. Notice is deemed given when posted
2. The parties may agree otherwise in writing

**Failure mode:** Tool treats "unless" clause as modifier rather than separate duty.

---

## Ship call

Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

---

## Tripwire

Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

---

## How a stranger uses this auditor

1. Describe your lease-line splitting tool and what it's supposed to do
2. Paste three real lease lines where it fails (especially "provided that" or conditional constructions)
3. The auditor walks all five checks, scoring each 0–4
4. Each finding names the measurement that would confirm it
5. You receive: a scored audit, a severity story, a ship/hold call with owner, and a tripwire with a number and danger line

---

## Execution

See [prompts/check-walk-pack.md](../prompts/check-walk-pack.md) for the five standalone prompts that operationalize each check.
