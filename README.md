# actions-lark - Github Action

Actions Any failed operation can be implemented with the tool to implement lark notifications

## Example usage

Then you can use the following example to create a workflow file in your repository.

```yaml
name: Test CI & CD
on:
  push:
    branches:

jobs:
  deps-update:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v3

      - name: Integration failure notifications
        if: ${{ failure() }}
        uses: baerwang/actions-lark@main
        with:
          lark-bot-notify-webhook: ${{ secrets.LARK_BOT_NOTIFY_WEBHOOK_FME }}
          title: "Integration test failure 💥"
          action-link: https://github.com/${{ github.repository }}/actions/runs/${{ github.run_id }}