# DynamoDB

A managed NoSQL database. Note that the main entity you will interact with are tables. DynamoDB doesn't have a notion of "databases".

- `aws dynamodb list-tables --region us-east-1 --output table` - list tables
- `aws dynamodb scan --region us-east-1 --table-name <table-name>` - get content of table