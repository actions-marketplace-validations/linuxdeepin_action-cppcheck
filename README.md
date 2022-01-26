# action-cppcheck

Check pull request with cppcheck and post result to review comments.

![Screenshot](screenshot.png)

## Inputs

```yaml
inputs:
  github_token:
    description: "action github token"
    required: true
  repository:
    description: "owner and repository name"
    required: true
  pull_request_id:
    description: "pull request id"
    required: true
  allow_approve:
    description: "allow submit approve review"
    required: true
    default: true
```

## Example

github action config

```yaml
name: cppcheck
on:
  pull_request:
    types: [opened, synchronize]
jobs:
  cppchceck:
    name: cppcheck
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: myml/action-cppcheck@main
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          repository: ${{ github.repository }}
          pull_request_id: ${{ github.event.number }}
```

## Allow approval

See: https://github.blog/changelog/2022-01-14-github-actions-prevent-github-actions-from-approving-pull-requests/
