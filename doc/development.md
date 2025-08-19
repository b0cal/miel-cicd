# Development workflow

## Branching model

We follow a Gitflow branching model for its clear history and its structured
release management.

The branching model is structured as followed:

```
├── main
├── dev
    ├── hotfix
    │   ├── hotfix/bugfix1
    │   └── hotfix/bugfix2
    ├── feat
    │  ├── feat/feature1
    │  └── feat/feature2
    └── release
```

- `main`: Stores official release history, commits should be tagged with a
  semantic version number (starting at v0.1).
- `dev`: Integration branch, created from main.
- `release`: Once enough features in `develop`, fork a `release` branch off of
  `develop`, merge into `develop` and `main` when done. Naming convention is
  adjectives linked to honey texture
- `feat`: Created from `develop`, merges into `develop` when completed
- `hotfix`: When and issue is detected in `main` branch, create a hotfix branch
  from main, once completed, merge into both `develop` and `main`

![More info here](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

## Commit message convention

Should be structured as followed:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

With the following structural elements:

- **fix**: commit of `type` _fix_ patches a bug in codebase
- **feat**: commit of `type` _feat_ introduces new feature to the codebase
- **BREAKING CHANGE**: commit with _BREAKING CHANGE_ `footer` or appends _!_
  after type/scope introduces a breaking API change. Can be part of any type
- `types` other than _fix_ and _feat_ are allowed
  - Non exhaustive list: _build_, _doc_, _refactor_, _test_
- `footers` other than _BREAKING CHANGE_ should follow a `key: value` format

![More info](https://www.conventionalcommits.org/en/v1.0.0/#summary)

## Code review and pull requests

As we're working with a small team, handling very small PR is not manageable,
try to make PRs as small as possible (so no full features at once), but avoid
PRs of less than 50 lines of code. Aim is to point out issues ASAP without
overloading the team with review duties

Every PR from `feature` into `develop` should be reviewed by at least one other
team member.

Every change made to `main` or `release` branches should be reviewed by all team
members.

Rotate reviewers on every other PR so the team keeps a global overview of the
project.

![More info](https://blog.mergify.com/pull-request-review-best-practices-code-excellence/)

## Testing expectations

As Rust integrates testing well, adopting a test-driven development process
should benefit keeping error rate low.

_Reminder:_ Start by writing a test that won't pass (feature not implemented),
then you implement the minimal code to make the test pass, then you refactor and
add whatever while keeping tests passing.

In optimal situation, every Rust file should contain a unit testing section.

Integration testing should be done at the same level as the binary code (so not
in the lib).

Performance testing must be done by integrating tools in the source code and
using conditional compilation to run them only in debug mode.
