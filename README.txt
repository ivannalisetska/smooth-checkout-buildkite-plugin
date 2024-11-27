# Improved Checkout Buildkite Plugin

A refined plugin for handling repository checkouts in Buildkite pipelines.

## Features

- Checkout multiple repositories.
- Support for custom SSH key paths.
- Customizable checkout directory.
- Option to skip checkout or delete the checkout directory after the build.
- Supports Git providers like GitHub and GitLab.

## Requirements

- Buildkite Agent with plugin support.
- `git` installed on the agent.
- Optional: `git-lfs` if using Git LFS.

## Configuration

### Plugin Configuration Example

```yaml
steps:
  - label: "Build Project"
    command: "build.sh"
    plugins:
      - your-org/improved-checkout#v1.0.0:
          checkout_path: "/path/to/checkout"
          delete_checkout: true
          repos:
            - url: "git@github.com:your-org/your-repo.git"
              ref: "main"
              ssh_key_path: "/path/to/ssh_key"
              clone_flags:
                - "--depth"
                - "1"
            - url: "git@gitlab.com:your-org/another-repo.git"
              ref: "develop"
