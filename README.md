## setup profile for localstack

```
$ aws configure --profile localstack
AWS Access Key ID [None]: test
AWS Secret Access Key [None]: test
Default region name [None]: ap-northeast-1
Default output format [None]: json

$ grep "localstack" -A 3 ~/.aws/config
[profile localstack]
region = ap-northeast-1
output = json
```

## using localstack CLI

```
$ pip install --upgrade pip

$ pip install localstack

$ localstack start
```

## using docker compose

```
$ docker compose up -d
```

## using aws cli

```
$ aws --endpoint-url=http://localhost:4566 s3 mb s3://sample-bucket --profile localstack

$ aws --endpoint-url=http://localhost:4566 s3 ls --profile localstack
2022-08-14 13:23:25 sample-bucket

$ touch sample.txt

$ aws s3 --endpoint-url=http://localhost:4566 cp sample.txt s3://sample-bucket/sample-dir/ --profile localstack
upload: ./sample.txt to s3://sample-bucket/sample-dir/sample.txt

$ aws s3 --endpoint-url=http://localhost:4566 ls s3://sample-bucket/sample-dir/ --profile localstack
2022-08-14 14:05:04          0 sample.txt
```

## using awscli-local

```
$ pip install awscli-local

# https://docs.localstack.cloud/aws/s3/
$ awslocal s3api create-bucket --bucket sample-bucket

$ awslocal s3api list-buckets
{
    "Buckets": [
        {
            "Name": "sample-bucket",
            "CreationDate": "2022-08-14T04:23:25+00:00"
        }
    ],
    "Owner": {
        "DisplayName": "webfile",
        "ID": "bcaf1ffd86f41161ca5fb16fd081034f"
    }
}
```
