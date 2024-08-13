# Lambda

- `aws lambda list-functions --region <region>` (list all lambdas)
- `aws lambda get-function --function-name <name> --region <region>` (get information about the lambda including its code!)
- `aws lambda get-policy --function-name <name> --region <region>` (get the policy attached to the lambda)
- `aws lambda invoke --function-name <name> --region <region> output.txt` (run the lambda)

Figuring out the URL to talk to a Lambda:
    - Gathering information:
        - We can run the above `get-policy` command which may show us that the lambda is invoked by an API Gateway
        - We can run `aws apigateway get-rest-apis` to directly check out the API Gateways
        - Next, we can run `aws apigateway get-rest-api --rest-api-id <api-gateway-id>` which shows more information about the Gateway
    - Putting it together: 
        - Lambda URLs have the shape of https://[NAME].execute-api.[REGION].amazonaws.com
        - [NAME] => the API Gateway ID
            - e.g. say we have an API Gateway ARN like `arn:aws:execute-api:us-east-1:999143725571:rsd847a1e9`
            - Here, the API Gateway ID would be `rsd847a1e9` and we could access the Lambda via the API Gateway at: https://rsd847a1e9.execute-api.[REGION].amazonaws.com
