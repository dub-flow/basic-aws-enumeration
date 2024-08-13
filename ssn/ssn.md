# Simple Notification Service (SSN)

Enables the distribution of messages and notifcations across different platforms and endpoints.

- `aws sns subscribe --topic-arn <arn> --region us-east-1 --protocol email --notification-endpoint bla@blub.com` - subscribe to an SNS topic (you have to provide a valid email address that you control!)
    - Check your inbox and click on the link in the confirmation email
    - Now, you should start receiving emails whenever stuff is pushed to the SNS topic