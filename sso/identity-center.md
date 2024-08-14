# IAM Identity Center (Formerly known as AWS SSO)

* Example Use Cases:
    - Allows managing user accounts across several AWS accounts
    - SSO: Allows e.g. to login into your AWS account using Okta or Active Directory

* How to find the URL of the Access Portal?
    - The URL for the AWS IAM Identity Cneter looks as follows: `d-xxxxxxxxxx.awsapps.com/start`
    - This mmeans we need to obtain the `d-` value somehow, e.g. from a hacked Kubernetes pod
    - Alternatievely, we could try to guess or bruteforce this value since most organisations customize this Identity by replacing it with their company name

* Basic Enumeration:
    - `aws sso-admin list-instances --region <region>` - list the AWS SSO instance
    - `aws sso-admin list-permission-sets --instance-arn <sso_instance_arn> --region <region>` - List the permission sets of an SSO instance
    - `aws sso-admin describe-permission-set --instance-arn <sso_instance_arn> --permission-set-arn <permission_set_arn> --region <region>` - Get the details of a specific permission set