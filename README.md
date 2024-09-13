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
    uses: UW-Macrostrat/build-push/.github/workflows/build-push.yaml@main
    secrets: inherit
    with:
      image: 'hub.opensciencegrid.org/macrostrat/traefik-log-exporter'
      context: <optional - remove this line if the context is root>
      path: <optional - remove this line if the dockerfile is at the root of the context>
```
