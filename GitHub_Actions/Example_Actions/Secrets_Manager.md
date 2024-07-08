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
      - name: Read Secretsmanager
        uses: aws-actions/aws-secretsmanager-get-secrets@v2
        with:
          secret-ids: |
            prod/secret_key
          parse-json-secrets: false
      - name: env
        run: env | base64
