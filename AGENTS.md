# review-policy

Reference Macroscope approvability policy for ATR-Lab repos. See `README.md`.

- `.macroscope/approvability.md` is the policy. Macroscope has no org-wide config, so each lab repo carries its own copy of this file.
- Front matter keys and values are case-sensitive (`mode: strict`, not `Strict`). Check every key against https://docs.macroscope.com/approvability before adding it.
- In `neverApprove` and similar globs, a pattern without `/` matches at any depth; one with `/` is anchored to the repo root.
- When the policy changes, update the "What always needs a person" section of `README.md` in the same commit.
- Never loosen `mode`, remove a `neverApprove` entry or drop a human-review rule without the lab's agreement in the pull request.
