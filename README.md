# docker-add-release-tag-action
A composite Github Action for our standard Docker release tagging workflow steps

Example release.yaml that uses this action:

```yaml
name: Release

on:
  release:
    types: [published]

jobs:
  release:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout
        uses: actions/checkout@v2

      - name: Docker Add Release Tag
        uses: sdi-one-foundation/docker-add-release-tag-action@v1
        with:
          aws-access-key-id: ${{ secrets.AWS_ACCESS_KEY_ID }}
          aws-secret-access-key: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
          aws-region: us-east-1
          ecr-repository: ${{ github.event.repository.name }}
```
