---
mode: strict
neverApprove:
  - ".github/workflows/**"
  - "CODEOWNERS"
  - ".macroscope/**"
---

Use Macroscope's default approvability criteria.

Require human review for changes that:

- Alter research evaluation metrics, ground-truth labels,
  experimental protocols, or reported results.
- Introduce or modify safety-critical robotic control.
- Change credentials, access control, or deployment security.
- Disable or suppress static-analysis diagnostics.
- Modify existing behavior without sufficient verification.

Documentation updates, tests, and narrowly scoped fixes
remain eligible for automatic approval when correctness
checks pass and no material uncertainty exists.
