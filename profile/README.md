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
%%{init: {"rmartinez-labs":"palette","theme":"base","themeVariables":{"fontFamily":"IBM Plex Sans Variable, IBM Plex Sans, Inter Variable, Segoe UI, Roboto, Helvetica, Arial","primaryColor":"#eff3f4","primaryTextColor":"#141925","primaryBorderColor":"#6868dc","secondaryColor":"#e6e6fa","secondaryTextColor":"#141925","secondaryBorderColor":"#6868dc","tertiaryColor":"#f7f8f8","tertiaryTextColor":"#141925","tertiaryBorderColor":"#6868dc","mainBkg":"#eff3f4","nodeBorder":"#6868dc","clusterBkg":"#f7f8f8","clusterBorder":"#6868dc","noteBkgColor":"#e3b341","noteTextColor":"#141925","noteBorderColor":"#e3b341","lineColor":"#6868dc","arrowheadColor":"#6868dc","defaultLinkColor":"#6868dc","textColor":"#6868dc","titleColor":"#6868dc","edgeLabelBackground":"#f7f8f8","actorBkg":"#eff3f4","actorBorder":"#6868dc","actorTextColor":"#141925","actorLineColor":"#6868dc","signalColor":"#6868dc","signalTextColor":"#6868dc","labelBoxBkgColor":"#eff3f4","labelBoxBorderColor":"#6868dc","labelTextColor":"#141925","loopTextColor":"#6868dc","activationBkgColor":"#e6e6fa","activationBorderColor":"#6868dc","sequenceNumberColor":"#ffffff","stateBkg":"#eff3f4","stateLabelColor":"#141925","transitionColor":"#6868dc","transitionLabelColor":"#141925","labelBackgroundColor":"#f7f8f8","compositeBackground":"#f7f8f8","compositeTitleBackground":"#eff3f4","compositeBorder":"#6868dc","altBackground":"#e6e6fa","attributeBackgroundColorOdd":"#f7f8f8","attributeBackgroundColorEven":"#eff3f4","relationColor":"#6868dc","relationLabelBackground":"#f7f8f8","relationLabelColor":"#141925","classText":"#141925","sectionBkgColor":"#e6e6fa","altSectionBkgColor":"#f7f8f8","sectionBkgColor2":"#eff3f4","excludeBkgColor":"#f1f3f4","taskBkgColor":"#6868dc","taskBorderColor":"#141925","taskTextColor":"#ffffff","taskTextLightColor":"#ffffff","taskTextDarkColor":"#141925","taskTextOutsideColor":"#6868dc","activeTaskBkgColor":"#b4b4f2","activeTaskBorderColor":"#6868dc","doneTaskBkgColor":"#f1f3f4","doneTaskBorderColor":"#536471","critBkgColor":"#e3b341","critBorderColor":"#c62f2f","todayLineColor":"#e3b341","gridColor":"#6868dc","fillType0":"#eff3f4","fillType1":"#e6e6fa","fillType2":"#f7f8f8","fillType3":"#d6d6fa","fillType4":"#eff3f4","fillType5":"#e6e6fa","fillType6":"#f7f8f8","fillType7":"#d6d6fa","git0":"#4343b0","git1":"#8f8fe8","git2":"#e3b341","git3":"#536471","git4":"#b4b4f2","git5":"#4343b0","git6":"#8f8fe8","git7":"#536471","gitBranchLabel0":"#ffffff","gitBranchLabel1":"#141925","gitBranchLabel2":"#141925","gitBranchLabel3":"#ffffff","gitBranchLabel4":"#141925","gitBranchLabel5":"#ffffff","gitBranchLabel6":"#141925","gitBranchLabel7":"#ffffff","commitLabelColor":"#141925","commitLabelBackground":"#eff3f4","tagLabelColor":"#141925","tagLabelBackground":"#e6e6fa","tagLabelBorder":"#6868dc"},"themeCSS":".labelBkg{background-color:#f7f8f8;color:#141925}.task .label,.journey-section .label{color:#141925}.taskText.critText0,.taskText.critText1,.taskText.critText2,.taskText.critText3{fill:#141925}"}}%%
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
