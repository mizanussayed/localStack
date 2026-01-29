## LocalStack
LocalStack is a fully functional local AWS cloud stack. This means you can develop and test your cloud applications offline without connecting to a real AWS cloud environment. LocalStack provides an easy-to-use test/mocking framework for developing cloud applications.

### Features
- Emulates a wide range of AWS services including S3, Lambda, DynamoDB, SNS, SQS, and more.
- Supports most AWS SDKs and CLI commands.
- Easy to set up and run using Docker.
- Ideal for local development and testing of cloud applications.
### Installation
To install LocalStack, you can use Docker. Run the following command:
```bash
docker run -d -p 4566:4566 -p 4571:4571 localstack/localstack
```
## to run LocalStack using Docker Compose, create a `docker-compose.yml` file with the following content:
```yaml
version: '3.8'
services:
  localstack:
    image: localstack/localstack
    ports:
      - "4566:4566"
      - "4571:4571"
    environment:
      - SERVICES=s3,lambda,dynamodb,sns,sqs
      - DEBUG=1
      - WEB_UI=1 # Enable the web interface
    volumes:
      - "./localstack_data:/tmp/localstack"
```
Then, run the following command to start LocalStack:
```bash
docker-compose up -d
```
### Configuration
to install awscli-local, you can use pip:
```bash
pip install awscli-local
```
This tool allows you to interact with LocalStack using AWS CLI commands prefixed with `awslocal`. For example, to list S3 buckets in LocalStack, you can run:
```bash
awslocal s3 ls
```
### Usage
Once LocalStack is running, you can interact with it using AWS CLI or SDKs. For example, to create an S3 bucket, you can use the following AWS CLI command:
```bash
aws --endpoint-url=http://localhost:4566 s3 mb s3://my-bucket
```
# using awscli-local, you can run:
```bash
awslocal s3 mb s3://my-bucket
```

# nside docker container, install awscli-local and run:
```bash
pip install awscli-local
awslocal s3 mb s3://my-bucket
```
# Web Interface
TO access the web interface at `http://localhost:8080`.
### Documentation

