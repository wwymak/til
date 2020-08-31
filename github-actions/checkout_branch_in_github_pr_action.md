# Check out branch in github action

Github actions can be triggered by various events such as pull requests as well as push. One useful github action is [checkout repo](https://github.com/actions/checkout). However, if you want to e.g modify or add a file in the github action flow and commit this back to the branch, you would need to checkout the branch -- by default if the action is triggered by a pull request the action checks out the detached HEAD.

To checkout a branch, just change the `ref` option to `${{ github.head_ref }}`

e.g.
```yaml
build:
  runs-on: ubuntu-latest
  steps:
  - name: Check out repo
    uses: actions/checkout@v2
    with:
      fetch-depth: 0
      ref: ${{ github.head_ref }}
```
