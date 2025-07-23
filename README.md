# Setup gh cli action

> **Note:** This is a fork of [ksivamuthu/actions-setup-gh-cli](https://github.com/ksivamuthu/actions-setup-gh-cli)

This repo contains the github actions for installing gh cli in self hosted runners. The gh cli is available in the github hosted cloud runners. In self hosted runners, if you want to use the gh cli, you can use this action to install the gh cli. 

## Usage

To install the gh cli, use the actions as below:

   ```yaml
    build:
      runs-on: [self-hosted]
      steps:
        - uses: actions/checkout@v2
        - name: Install the gh cli
          uses: heyhayes/actions-setup-gh-cli@<VERSION>
          with:
            version: 2.24.3
            token: ${{ secrets.GITHUB_TOKEN }}  # Optional: to avoid rate limits
        - run: |
            gh version
   ```

## Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `version` | gh cli version to download | No | Latest version |
| `archive_format` | Format of the archive (tar.gz or zip) | No | tar.gz |
| `token` | GitHub token to avoid rate limits when fetching latest version | No | - |

## Rate Limits

When no specific version is provided, this action fetches the latest version from the GitHub API. To avoid rate limits, especially in high-usage scenarios, provide a `token` input with a GitHub token (typically `${{ secrets.GITHUB_TOKEN }}`).
