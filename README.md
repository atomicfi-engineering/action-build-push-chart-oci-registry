# GitHub Action:Build and Push Chart to OCI Registry

Builds and pushes a Helm chart to an OCI registry

```yaml
- uses: atomicfi-engineering/action-build-push-chart-oci-registry@undefined
  with:
    # Path to chart. Required.
    # Default:
    chart-path: ""
    # Sets whether or not to update dependencies before packaging
    # Default: true
    update-dependencies: ""
    # URL of registry, excluding the protocol. Required.
    # Default:
    registry-url: ""
    # Repository in registry to push to
    # Default: charts
    repository: ""
    # Username to login to registry
    # Default:
    username: ""
    # Password to login to registry
    # Default:
    password: ""
    # Enables step to delete all `*.tgz` files
    # Default: true
    delete-tgzs: ""
```

| **Input**                 | **Description**                                             | **Default** | **Required** |
| :------------------------ | :---------------------------------------------------------- | :---------: | :----------: |
| **`chart-path`**          | Path to chart                                               |             |   **true**   |
| **`update-dependencies`** | Sets whether or not to update dependencies before packaging | `true`      |   **false**  |
| **`registry-url`**        | URL of registry, excluding the protocol                     |             |   **true**   |
| **`repository`**          | Repository in registry to push to                           | `charts`    |   **false**  |
| **`username`**            | Username to login to registry                               |             |   **false**  |
| **`password`**            | Password to login to registry                               |             |   **false**  |
| **`delete-tgzs`**         | Enables step to delete all `*.tgz` files                    | `true`      |   **false**  |

### Example usage

```yaml
name: Build and push chart to registry
on:
  push:
    branches:
      - main
jobs:
  build-and-push-helm-chart:
    runs-on: ubuntu-latest
    name: Build and push chart to registry
    steps:
      - uses: atomicfi-engineering/action-build-push-chart-oci-registry
        with:
          chart-path: charts/chart-name
          registry-url: registry.example.com
          repository: charts
          username: admin
          password: hunter2
```
