<p align="center">
  <img src=".github/assets/header.png" alt="Review policy: When Macroscope may approve a lab pull request. Advanced Telerobotics Research Laboratory, Kent State University." width="100%">
</p>

<p align="center">
  <b>The lab's Macroscope approvability policy: which pull requests Macroscope may approve on its own, and which always wait for a person.</b><br>
  <sub>Advanced Telerobotics Research Laboratory · Department of Computer Science · Kent State University</sub>
</p>

<p align="center">
  <a href="LICENSE"><img alt="License: MIT" src="https://img.shields.io/badge/license-MIT-003976?style=flat-square"></a>
  <a href="https://docs.macroscope.com/approvability"><img alt="Macroscope: approvability" src="https://img.shields.io/badge/Macroscope-approvability-003976?style=flat-square"></a>
  <a href="https://www.atr.cs.kent.edu/"><img alt="Advanced Telerobotics Research Laboratory, Kent State University" src="https://img.shields.io/badge/ATR_Lab-Kent_State-003976?style=flat-square"></a>
  <img alt="Mode: strict" src="https://img.shields.io/badge/mode-strict-4A5868?style=flat-square">
  <img alt="Last reviewed Nov. 2026" src="https://img.shields.io/badge/last_reviewed-Nov._2026-4A5868?style=flat-square">
</p>

## Start here

<table>
  <tr>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/workshop-idea.png" width="44" alt=""><br>
      <b><a href="#how-it-works">How it works</a></b><br>
      <sub>Where Macroscope reads the policy and how it combines it with its own rules.</sub>
    </td>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/safety-shield.png" width="44" alt=""><br>
      <b><a href="#what-always-needs-a-person">What always needs a person</a></b><br>
      <sub>Paths and kinds of change that Macroscope never approves.</sub>
    </td>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/publication.png" width="44" alt=""><br>
      <b><a href="#what-can-be-approved">What can be approved</a></b><br>
      <sub>Docs, tests and small fixes that pass their checks.</sub>
    </td>
  </tr>
  <tr>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/code.png" width="44" alt=""><br>
      <b><a href=".macroscope/approvability.md">The policy file</a></b><br>
      <sub><code>.macroscope/approvability.md</code>, the only file Macroscope reads here.</sub>
    </td>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/milestone-flag.png" width="44" alt=""><br>
      <b><a href="#adding-the-policy-to-a-repo">Adding it to a repo</a></b><br>
      <sub>Copy the file in and turn approvability on.</sub>
    </td>
    <td width="33%" valign="top">
      <img src=".github/assets/icons/mechanical-gear.png" width="44" alt=""><br>
      <b><a href="#changing-the-policy">Changing the policy</a></b><br>
      <sub>Edit here first, then update the repos that carry a copy.</sub>
    </td>
  </tr>
</table>

## How it works

[Macroscope's approvability check](https://docs.macroscope.com/approvability) decides whether a pull request is safe to approve without a human reviewer. It reads `.macroscope/approvability.md` from the pull request's latest commit. The front matter sets options; the text below it adds rules on top of Macroscope's built-in criteria, which favor small, low-risk changes and already hold refactors, schema changes, security-sensitive code and breaking changes for a person.

Macroscope has no organization-wide config file, unlike [CodeRabbit](https://github.com/ATR-Lab/coderabbit). Each repo reads its own copy, so this repo is the reference copy that lab repos start from.

The policy runs in **strict** mode: Macroscope asks for a human review whenever meaningful risk remains, even if CI passes and the change looks correct.

## What always needs a person

Macroscope holds a pull request for a human reviewer, without running its eligibility check, when any changed file matches:

| Pattern | Covers |
|---|---|
| `.github/workflows/**` | CI and deployment workflows |
| `CODEOWNERS` | Who must review what, in any folder |
| `.macroscope/**` | Macroscope's own config, including this policy |

It also asks for a human review of any change that:

- alters research evaluation metrics, ground-truth labels, experimental protocols or reported results;
- introduces or modifies safety-critical robotic control;
- changes credentials, access control or deployment security;
- disables or suppresses static-analysis diagnostics;
- modifies existing behavior without enough verification.

A held pull request is not blocked from merging. To require a person before merge, use branch protection and required reviewers in GitHub.

## What can be approved

Documentation updates, tests and narrowly scoped fixes stay eligible for automatic approval when correctness checks pass and nothing material is uncertain. Macroscope never approves a pull request it opened itself.

## Adding the policy to a repo

1. Copy [`.macroscope/approvability.md`](.macroscope/approvability.md) into the repo at the same path.
2. Turn approvability on for the repo in Macroscope under **Settings → Repos**.
3. Open the pull request. Macroscope always holds a pull request that adds or edits this file, so a lab member approves it.

To change a few rules for one repo, edit that repo's copy and say why in the pull request.

## Changing the policy

1. Edit [`.macroscope/approvability.md`](.macroscope/approvability.md). Front matter keys are case-sensitive; check them against the [supported fields](https://docs.macroscope.com/approvability). A pattern without `/` matches at any depth; one with `/` is anchored to the repo root.
2. Update [What always needs a person](#what-always-needs-a-person) in this README to match.
3. Open a pull request. Once it merges, update the copies in the repos that carry the policy.

## Repo map

| Path | What it holds | Read it when |
|---|---|---|
| [`.macroscope/approvability.md`](.macroscope/approvability.md) | The approvability policy | You want to see or change what Macroscope may approve |
| [`.github/assets/`](.github/assets/) | The README header and icons | You restyle this page |
| [`LICENSE`](LICENSE) | The MIT License for this repo | You reuse the policy elsewhere |
| [`AGENTS.md`](AGENTS.md) | Instructions for coding agents (`CLAUDE.md` points to it) | You are, or you are directing, a coding agent |

## Contributing

Suggest a change by [opening an issue](https://github.com/ATR-Lab/review-policy/issues/new) or a pull request. A change here becomes the starting point for every lab repo, so say why in the pull request. To change what code reviews hold code to, edit [dev-guidelines](https://github.com/ATR-Lab/dev-guidelines) or the [CodeRabbit config](https://github.com/ATR-Lab/coderabbit) instead.

## License

The policy and docs in this repository are released under the [MIT License](LICENSE). The names and logos of the Advanced Telerobotics Research Laboratory and Kent State University are trademarks and are not covered by that license.

---

<p align="center">
  <sub><b>ATR Lab docs</b> ·
  <a href="https://github.com/ATR-Lab/about">About the lab</a> ·
  <a href="https://github.com/ATR-Lab/getting-started-atr-lab">Getting started</a> ·
  <a href="https://github.com/ATR-Lab/dev-guidelines">Dev guidelines</a> ·
  <a href="https://github.com/ATR-Lab/all-things-ros2">All things ROS 2</a> ·
  <a href="https://github.com/ATR-Lab">All repositories</a></sub><br>
  <sub>Advanced Telerobotics Research Laboratory · Department of Computer Science · Kent State University ·
  <a href="https://www.atr.cs.kent.edu/">www.atr.cs.kent.edu</a></sub>
</p>
