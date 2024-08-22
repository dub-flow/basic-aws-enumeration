# Amazon ActiveMQ

An enterprise messaging service that is simlar to SNS but e.g. guarantess that messages are saved and delivered.

* `aws mq list-brokers --region <region>` - list all brokers
* `aws mq describe-broker --broker-id <broker-id> --region <region>` - Get all info of a particular broker
    - The most interesting bits are the `PubliclyAccessible` flag (if set to `true`, then this is a public instance!)
    - `BrokerInstances` shows us the URL of the broker
* `aws mq list-users --broker-id <broker-id> --region <region>` - List all ActiveMQ users
* `aws mq describe-user --broker-id <broker-id> --username <user> --region <region>` - Get user info (not the password!)
* `aws mq list-configurations --region <region>` - Shows the configuration
    - The most interesting part is `AuthenticationStrategy` which shows if `LDAP authentication` or `Simple authentication` (i.e., username and password) is used
* `aws mq create-user --broker-id <broker-id> --console-access --password <pass> --username <user> --region <region>` - Create a user
* `aws mq update-user --broker-id <broker-id> --console-access --username <user> --password <pass> --region <region>` - Update a user 
* `aws mq reboot-broker --broker-id <broker-id> --region <region>` - Restart broker
    - may be required after adding/updating users