# Serverless LiteLLM-Proxy

This demo shows how to deploy [LiteLLM-Proxy](https://github.com/BerriAI/liteLLM-proxy) on AWS Lambda to provide an OpenAI compatable API for Amazon Bedrock.

## Pre-requisites

1. AWS CLI
2. AWS SAM CLI
3. Docker

## Build and deploy

Run the following commands to build and deploy this demo.

```shell
sam build

sam deploy --guided
```

You need to enter an random string for `ApiMasterKey` parameter. And take note of the `litellmProxyFunctionUrl` in output. You will use it in the testing.

## Test

Run this command to test it. Replace `litellmProxyFunctionUrl` and `ApiMasterKey` with the correct values. And you should see the response stream back.

```shell

curl <litellmProxyFunctionUrl>chat/completions \
    -H "Content-Type: application/json" \
    -H "Authorization: Bearer <ApiMasterKey>" \
    -d '{
            "model": "bedrock/anthropic.claude-v2",
            "messages": [
                {
                    "role": "system",
                    "content": "You are a helpful assistant."
                },
                {
                    "role": "user",
                    "content": "tell me a bedtime story about lambda and sqs"
                }
            ],
            "stream": true
        }'
```
