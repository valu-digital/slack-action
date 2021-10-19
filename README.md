
# Add `slack-message` to Github Workflows

Usage

```yaml
- uses: valu-digital/slack-action@master
  with:
      token: ${{ secrets.SLACK_TOKEN }}
      # or
      #webhook: ${{ secrets.SLACK_WEBHOOK }}
      channel: "#channel" # Channel to send the message to
```

This puts the `slack-message` command to the PATH in your Github Workflows and
allows which can be used from any steps.


Example:

```yaml
- name: Build and deploy
  run: |
	slack-message "Starting deploy"

	npm ci
	npm run deploy

	slack-message "App deployed"
```

Failure notifications

```yaml
- name: Notify about failure
  if: failure()
  run: slack-message "Deploy failed"
```