# runner-cleanup

_Modified version of [this action](https://github.com/easimon/maximize-build-space/)_

The main changes between the linked repo and this action is that this action does not create a logical volume or resize the swap space. Additionally, all package/image removal is by default set to `true` so it can be used very simply.
Before running this action, a runner will have `~18GB` of free disk. Afterwards, there will be `~48GB` free.

## Usage

```yaml
name: Action
on: push

jobs:
  build:
    name: Job
    runs-on: ubuntu-latest
    steps:
      ## cleanup runner
      - name: Cleanup Runner
        id: runner_cleanup
        uses: stacks-network/runner-cleanup@main
```

## Inputs

All inputs are optional and default to the following.

```yaml
remove-dotnet:
  description: "Removes .NET runtime and libraries. (frees ~17 GB)"
  required: false
  default: "true"
remove-android:
  description: "Removes Android SDKs and Tools. (frees ~11 GB)"
  required: false
  default: "true"
remove-haskell:
  description: "Removes GHC (Haskell) artifacts. (frees ~2.7 GB)"
  required: false
  default: "true"
remove-codeql:
  description: "Removes CodeQL Action Bundles. (frees ~5.4 GB)"
  required: false
  default: "true"
remove-docker-images:
  description: "Removes cached Docker images. (frees ~3 GB)"
  required: false
  default: "true"
```
