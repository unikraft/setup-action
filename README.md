# setup-action

Install the Unikraft CLI from GitHub releases and optionally log in to Unikraft Cloud.

## Usage

```yaml
- name: Install Unikraft CLI
  uses: unikraft/setup-action@v1
```

Pin a specific version or use the prerelease channel:

```yaml
- name: Install Unikraft CLI (pinned)
  uses: unikraft/setup-action@v1
  with:
    version: 0.1.0-staging.71

- name: Install Unikraft CLI (dev)
  uses: unikraft/setup-action@v1
  with:
    version: dev
```

Log in to Unikraft Cloud:

```yaml
- name: Install and login
  uses: unikraft/setup-action@v1
  with:
    version: dev
    token: ${{ secrets.UKC_TOKEN }}
    organization: my-org
```

## Inputs

- `version`: Version to install (`latest`, `dev`, or a release tag). Default: `latest`.
- `github-token`: GitHub token used by `gh` for release resolution and downloads. Default: `${{ github.token }}`.
- `token`: Authentication token for Unikraft login. Default: empty.
- `organization`: Organization to associate the login with. Default: empty.

## Outputs

- `version`: Resolved release tag that was installed.

## Notes

- `organization` requires `token`.
- The action uses `gh` and `jq`, which are available on GitHub-hosted runners.
