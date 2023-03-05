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
      - uses: bugbundle/commits@v1
```

> **Note** You can check previous commits by adding the `fetch-depth` parameters while using `actions/checkout`.