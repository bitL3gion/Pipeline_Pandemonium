```
name: First Workflow
on: push
jobs:
  first-job:
    env:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_KEY }}
      AWS_REGION: "us-east-1"
    runs-on: ubuntu-latest
    steps:
      - name: AWS STS Whoami
        run: aws sts get-caller-identity
      - name: AWS Assume Role
        uses: aws-actions/configure-aws-credentials@v4
        with:
          aws-region: us-east-1
          role-to-assume: <ROLE_ARN>
          role-duration-seconds: 1200
          role-skip-session-tagging: true
      - name: AWS STS Whoami 2
        run: aws sts get-caller-identity
```
