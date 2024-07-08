name: First Workflow
on: pull_request
permissions:
  id-token: write
  contents: write
  pull-requests: write
jobs:
  first-job:
    runs-on: ubuntu-latest
    steps:
      - name: Configure AWS Creds
        uses: aws-actions/configure-aws-credentials@v4
        with:
          role-to-assume: ${{ secrets.AWS_DEV_GITHUB_ACTION_ROLE }}
          aws-region: us-east-1
          role-session-name: OIDCSession
      - name: AWS STS Whoami
        run: aws sts get-caller-identity
