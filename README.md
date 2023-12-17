# Create release action

This action creates a release in GitHub. If a slack bot token is provided, it will also send a message to a slack channel.

## Inputs

- `use-sem-ver`: Use semantic versioning
- `tag`: Tag to use for the release

### Slack inputs

- `SLACK_BOT_TOKEN`: Slack bot token
- `title`: Title of the release
- `hide-authors`: Hide authors in release notes
- `hide-prs`: Hide PRs in release notes
- `hide-full-change-log-link`: Hide full changelog link in release notes
- `hide-title`: Hide title in release notes
- `add-divider`: Add divider in release notes
- `channel`: Channel to publish to
- `repost-channels`: Channels to repost to (`;` separated)

## Outputs

- `version`: The version of the release

## Example usage

> [!IMPORTANT]
> You will need to set `GITHUB_TOKEN` in environment variables for this action to work and you will need to provide write access to the repository for the bot user.

```yaml
name: Create release
on:
  push:
    branches:
      - main
env:
  GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
jobs:
  create-release:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - name: Create release
        uses: nbotond20/create-release@v1.1.1
        with:
          use-sem-ver: true
```
