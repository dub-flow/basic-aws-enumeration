# Secrets Manager

- `aws secretsmanager list-secrets --region <region>` - list secrets
- `aws secretsmanager get-secret-value --secret-id <secret-arn> --query SecretString --output text --region <region>` - get secret value (of the latest version)
    - If we want to get the value of an older version, we have to provide the: `--version-id <version-id>`
- `aws secretsmanager describe-secret --secret-id <secret-arn> --region <region>` - shows more information about a secret, such as if different versions exist

