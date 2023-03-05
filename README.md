# Commits linter

Checks the commits made by developers in a repository to ensure they adhere to [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/). 

## How to use

```yaml
name: Check current commit
on: [push]

jobs:
  dev:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
      - uses: bugbundle/commits@v1.1.0
```

> **Note** You can check previous commits by adding the `fetch-depth` parameter while using `actions/checkout`.

### Inputs

- `git-range`, default 'HEAD':
  Range of commits.


### Outputs

- `patch`, Count of patch commits
- `minor`, Count of minor commits
- `major`, Count of major commits

### Pull request integration

```yaml
name: Check current commit
on: [pull_request]

jobs:
  dev:
    runs-on: ubuntu-22.04
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: ${{ github.event.pull_request.commits }}
          ref: ${{ github.event.pull_request.head.sha }}
      - uses: bugbundle/commits@v1.1.0
        id: commits
      - run: echo ${{ steps.commits.outputs.major }}.${{ steps.commits.outputs.minor }}.${{ steps.commits.outputs.patch }}
```