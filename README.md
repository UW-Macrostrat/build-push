# build-push

Macrostrat drop in image build and pusher with built-in tagging scheme designed for kubernetes services.

## Usage

Copy the following into `.github/workflows/build-push.yml`:

```yaml
name: Build image

on:
  push:
    branches: ["main"]
    tags:
      - 'v*.*.*' # glob for semver tags (including prereleases)
  pull_request:
    branches: [main]

jobs:
  call-build-image:
    uses: ./.github/workflows/build-image-reusable.yaml
    with:
      image: 'hub.opensciencegrid.org/macrostrat/<x>'
      path: <optional>
      context: <optional
      username: ${{ vars.HARBOR_CLI_NAME }}
      password: ${{ secrets.HARBOR_CLI_SECRET }}
```
