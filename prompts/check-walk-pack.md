# Lease Duty-Splitting Auditor — Five-Check Prompt Pack

Use these five prompts to audit any lease-line splitting tool. Each check ends with the measurement it demands. Paste one prompt at a time into any chat model, supply your own failing lease lines, and record the score.

---

## Check 1: Unowned

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to check whether every splitting rule has a named owner who is accountable when it fails.
>
> Here is a failing input from my tool:
>
> **Worked example (Harbor Lease):**
> "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
>
> The tool merged two duties so the wrong party looks responsible. No one owned the rule that should have caught this.
>
> **Your task:**
> 1. List every splitting rule the tool uses for conditional clauses like "provided that."
> 2. For each rule, name the owner accountable for its correctness — or mark it "unowned."
> 3. Count how many rules are unowned.
>
> **Measurement:** Report the count of unowned splitting rules. Zero means pass; any positive number means fail.

---

## Check 2: Copies

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to check whether the tool duplicates logic in multiple places, creating drift risk.
>
> Here are failing inputs from my tool:
>
> **Worked examples (Harbor Lease):**
> - "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
> - "Fees accrue daily; provided, however, that the cap in §4.2 still applies."
> - "Notice is deemed given when posted, unless the parties agree otherwise in writing."
>
> **Your task:**
> 1. Identify every place in the tool where conditional-clause splitting logic is defined.
> 2. Check whether the same logic appears in more than one location.
> 3. Note any inconsistencies between copies.
>
> **Measurement:** Report the number of duplicate logic locations. One location means pass; two or more means fail.

---

## Check 3: Room

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to check whether the tool has headroom to handle edge cases — nested conditionals, unusual punctuation, variant phrasing.
>
> Here are failing inputs from my tool:
>
> **Worked examples (Harbor Lease):**
> - "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
> - "Fees accrue daily; provided, however, that the cap in §4.2 still applies."
> - "Notice is deemed given when posted, unless the parties agree otherwise in writing."
>
> These come from old scanned leases with nested "provided that" lines.
>
> **Your task:**
> 1. List the conditional patterns the tool currently handles.
> 2. List edge-case patterns it does not handle (e.g., "provided, however," or "unless ... in writing").
> 3. Estimate what percentage of real lease lines fall outside current coverage.
>
> **Measurement:** Report the estimated percentage of lease lines the tool cannot split correctly. Under 5% means pass; 5% or higher means fail.

---

## Check 4: Stitch

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to check whether the tool correctly stitches split duties back to the right party — or whether it fuses duties and assigns responsibility to the wrong side.
>
> Here is a failing input from my tool:
>
> **Worked example (Harbor Lease):**
> "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
>
> The tool merged two duties so the wrong party looks responsible. A partner could sign a summary that puts repair duty on the wrong side.
>
> **Your task:**
> 1. Split this line into its component duties.
> 2. Assign each duty to the correct party (Tenant or Landlord).
> 3. Compare your split to the tool's output. Identify any fused or mis-assigned duties.
>
> **Measurement:** Report the number of duties assigned to the wrong party. Zero means pass; any positive number means fail.

---

## Check 5: Ablation

**Prompt:**

> I have a lease tool that splits contract lines into separate duties. I need to check whether removing any single component breaks the tool entirely — a sign of fragile architecture.
>
> Here are failing inputs from my tool:
>
> **Worked examples (Harbor Lease):**
> - "Tenant shall repair the roof provided that Landlord funds materials within 10 days."
> - "Fees accrue daily; provided, however, that the cap in §4.2 still applies."
> - "Notice is deemed given when posted, unless the parties agree otherwise in writing."
>
> **Your task:**
> 1. Identify the key components of the splitting logic (parser, rule engine, party-assignment module, etc.).
> 2. For each component, describe what happens if it is removed or disabled.
> 3. Count how many components, if removed, cause total failure (not just degraded performance).
>
> **Measurement:** Report the number of single-point-of-failure components. Zero means pass; any positive number means fail.

---

## Scoring Summary

After running all five checks, record your scores:

| Check | Score | Pass Threshold |
|-------|-------|----------------|
| Unowned | ___ | 0 |
| Copies | ___ | 1 |
| Room | ___ | < 5% |
| Stitch | ___ | 0 |
| Ablation | ___ | 0 |

**Top crack for this audit:** Stitch — the tool fuses conditional duties and assigns responsibility to the wrong party.

**Ship call:** Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

**Tripwire:** Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

---

## Sample Asks

Use these as templates when a stranger brings their own lease-splitting tool:

1. "My lease parser keeps merging 'Lessee shall maintain insurance provided that Lessor supplies certificates' into one duty. Which check should I run first?"

2. "We have a contract tool that splits obligations but it chokes on 'notwithstanding any provision to the contrary' clauses. How do I score the Room check?"

3. "Our duty-splitter assigned 'Landlord shall reimburse provided Tenant submits receipts within 30 days' entirely to Tenant. Is that a Stitch failure?"

4. "I found three different regex patterns for 'provided that' in our codebase. Does that fail the Copies check?"

5. "If I disable our party-detection module, the whole splitter crashes. What's my Ablation score?"
