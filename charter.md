# Audit Charter: Lease tool that splits contract lines into separate duties

## Specimen under audit

**Tool:** Lease tool that splits contract lines into separate duties

**What goes wrong if this never gets fixed:** A partner signs a summary that puts repair duty on the wrong side

## Standard for pass

Each duty lands on its own line with the right party named

## Real inputs tested

**Source:** Harbor Lease sample contracts

**Usage reality:** Old scanned leases with nested "provided that" lines

### Pasted failing inputs

1. Tenant shall repair the roof provided that Landlord funds materials within 10 days.
2. Fees accrue daily; provided, however, that the cap in §4.2 still applies.
3. Notice is deemed given when posted, unless the parties agree otherwise in writing.

---

## Check findings

| Check | Score |
|-------|-------|
| Unowned | 1 |
| Copies | 1 |
| Room | 2 |
| Stitch | 4 |
| Ablation | 0 |

## Deciding check

**stitch**

The stitch check scores highest (4), making it the deciding factor in this audit. The tool fails to properly stitch conditional clauses back together after splitting, causing duties to fuse when "provided that" or similar hinge phrases appear.

---

## Call

Hold. Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

---

## Tripwire

Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

---

## Audit summary

This lease-splitting tool cannot ship. The stitch failure on "provided that" clauses means conditional duties merge, assigning responsibility to the wrong party. Until Priya owns the hinge check and all three Harbor Lease samples pass, the tool stays on hold. After release, Priya watches time-to-notice—any signed summary with a fused conditional duty before a partner catches it means the gap has already caused damage.
