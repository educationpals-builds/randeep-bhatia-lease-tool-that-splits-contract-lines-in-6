# The Five-Check Framework

This document explains the five principles used to audit whether a setup's checks actually split the work. The acronym **PRISM** captures the discipline:

---

## P — Partition the Space

Every input type the tool handles must land in exactly one bucket. For a lease-splitting tool, this means: simple clauses, conditional clauses with "provided that," nested conditionals, and exception phrases each get their own partition. If a clause type has no defined bucket, the tool guesses—and guesses merge duties.

---

## R — Run in Parallel

Each partition runs its own check independently. The "provided that" parser shouldn't wait on the simple-clause parser. When checks run in sequence and one fails silently, downstream checks inherit the error. Parallel runs surface failures where they happen.

---

## I — Individuate the Pattern

Each check must recognize its own pattern and nothing else. A check for "provided that" clauses should not also try to catch "unless" exceptions. When a single check tries to handle multiple patterns, it stitches them together—and stitching is where duties fuse.

---

## S — Stitch the Spectra

After checks run, their outputs must be stitched back into a coherent result. This is the danger zone. If the stitching logic doesn't know which check produced which output, it merges lines that should stay separate. The stitch check audits whether outputs from different checks stay distinct or collapse into one.

---

## M — Map What Each Head Sees

Every check must report what it saw and what it did. If a check silently passes a malformed clause, no one knows until a partner signs a wrong summary. Mapping means: each check logs its input, its decision, and its output—so a human can trace any fused duty back to the check that failed.

---

## The Anti-Pattern: Collapse to Monochrome

When a tool skips any of these principles, it collapses to monochrome: all inputs get the same treatment, all outputs look the same, and distinctions vanish. For lease splitting, monochrome means "Tenant shall repair the roof provided that Landlord funds materials" becomes one duty assigned to one party—when it should be two duties, two parties, two lines.

The five checks exist to prevent that collapse. Each letter in PRISM is a gate. Miss one, and the spectrum of duties flattens into a single wrong answer.
