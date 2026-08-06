# Lease tool that splits contract lines into separate duties

A lease tool is supposed to split contract lines into separate duties. On lines with "provided that", it still merges two duties so the wrong party looks responsible.

## Verdict

**Hold.** Without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template. Priya assigns ownership and requires a passing test against all three Harbor samples before ship.

## What goes wrong

A partner signs a summary that puts repair duty on the wrong side.

## The standard

Each duty lands on its own line with the right party named.

## Tripwire

Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

## Deciding check

**Stitch** — scored 4 (highest severity). The tool fails to separate duties when conditional clauses like "provided that" appear.

---

## One-paste rebuild block

Test the fix against these three Harbor Lease sample lines:

```
Tenant shall repair the roof provided that Landlord funds materials within 10 days.
Fees accrue daily; provided, however, that the cap in §4.2 still applies.
Notice is deemed given when posted, unless the parties agree otherwise in writing.
```

Each line must split into separate duties with the correct party assigned to each.

---

## Files in this repository

- [charter.md](charter.md) — Full audit with all five checks, findings, and the call
- [METHOD.md](METHOD.md) — The five-check framework
- [VERIFY.md](VERIFY.md) — How a stranger verifies their own lease-splitting setup

<!-- educationpals-build-verified -->
