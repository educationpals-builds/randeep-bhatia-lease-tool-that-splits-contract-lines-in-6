# Verify: Lease tool that splits contract lines into separate duties

Use this page to confirm the auditor surfaces the deciding-check finding and demands a numeric measurement for it.

---

## What you need

A lease-splitting setup you want to audit — your own tool that parses contract lines and assigns duties to parties.

---

## Run the verification

1. **Open /play** and paste a description of your lease-splitting setup:
   - What it is supposed to do (split contract lines into separate duties with the correct party named)
   - Who gets hurt when it fails (e.g., a partner signs a summary that puts repair duty on the wrong side)
   - Three real failing inputs — lines with nested "provided that" clauses where the tool merges duties incorrectly

2. **Walk the five checks.** The auditor will ask about each check in turn. Answer with what you observe in your own setup.

3. **Confirm the stitch finding surfaces.** The deciding check for the builder's audit was **stitch** — whether the tool correctly stitches conditional clauses back to the right party. The auditor must surface a finding about how your setup handles "provided that" hinge points.

4. **Confirm a numeric measurement is demanded.** The auditor must ask for a specific number that would confirm the stitch finding — not a vague "check if it works." For the builder's audit, the measurement was:
   > Watch time-to-notice: how many signed summaries go out before a fused conditional duty is caught by a partner. Priya owns it; if it's more than zero per month, the unowned gap has already caused damage.

   Your audit should demand an equivalent: a count, a threshold, and a watcher.

---

## Verification checklist

| Step | Expected result |
|------|-----------------|
| Paste your setup description | Auditor acknowledges the lease-splitting domain |
| Walk all five checks | Each check gets a rating and a finding |
| Stitch check surfaces | Auditor identifies how your tool handles conditional clauses |
| Numeric measurement demanded | Auditor asks for a specific number (e.g., fused duties per month) with a danger line and an owner |
| Call returned | Auditor gives ship / ship-with-conditions / hold with reasoning |
| Tripwire stated | Auditor names what to watch, the number that means trouble, and who watches it |

---

## If verification fails

- If the stitch finding does not surface: check that your input includes "provided that" or similar conditional clauses where duties could fuse.
- If no numeric measurement is demanded: the auditor may need more detail about your failure mode. Paste a specific example where the wrong party was assigned.
- If the call lacks an owner on conditions: re-run with explicit stakes (who signs the summary, who catches errors).

---

## Builder's worked example

The builder audited a lease tool processing Harbor Lease sample contracts. The tool failed on lines like:

> Tenant shall repair the roof provided that Landlord funds materials within 10 days.

The stitch check scored 4 (worst). The call was **Hold** — without an owner for the hinge check, there's no one accountable when it silently fails again on a new lease template.

Your audit should apply the same discipline to your own lease-splitting setup.
