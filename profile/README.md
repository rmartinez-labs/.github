<div align="center">

# rmartinez-labs

**A small lab that ships products on one shared platform.**

Every product starts from the same template, runs the same checks, and takes platform fixes through a release, never by copy and paste.

![ci](https://img.shields.io/badge/CI-self--hosted-1f2328?style=flat-square&logo=githubactions&logoColor=white)
![pins](https://img.shields.io/badge/actions-pinned%20by%20SHA-1f2328?style=flat-square)
![cooldown](https://img.shields.io/badge/updates-7%20day%20cooldown-1f2328?style=flat-square)

</div>

## How the pieces fit

```mermaid
flowchart TD
    W["shared workflows<br/>reusable CI"] -->|"pinned by SHA"| T["platform template"]
    W -->|"pinned by SHA"| P["products"]
    T -->|"copier copy"| P
    T -->|"tagged release,<br/>copier update"| P
    P -->|"asks for a<br/>platform change"| T
```

*The platform owns the shared parts. A product never edits them: it asks, and the next release brings the fix.*

## What we hold ourselves to

| Rule | In practice |
|---|---|
| Pinned, and not too fresh | every action by commit SHA, every tool and image by exact version, the newest one older than seven days |
| One gate per workflow | each workflow ends in a single `<Name> (required)` check, and branch protection reads only that |
| Security in every pipeline | secret scanning, dependency and image scans and workflow linting run from one shared set of workflows on every pull request |
| Releases from commits | conventional commit titles feed release-please; nobody tags by hand |
| Review before merge | the author never approves their own change; the verdict names the commit it read |
| Measure, then explain | a stated cause comes with the command that showed it |

The repositories are private for now.
