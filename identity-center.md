# IAM Identity Center 

Formerly known as AWS SSO.

* Example Use Cases:
    - Allows managing user accounts across several AWS accounts
    - SSO: Allows e.g. to login into your AWS account using Okta or Active Directory

* How to find the URL of the Access Portal?
    - The URL for the AWS IAM Identity Cneter looks as follows: `d-xxxxxxxxxx.awsapps.com/start`
    - This mmeans we need to obtain the `d-` value somehow, e.g. from a hacked Kubernetes pod
    - Alternatievely, we could try to guess or bruteforce this value since most organisations customize this Identity by replacing it with their company name

* AWS SSO – Device Code Phishing Attack (see https://blog.christophetd.fr/phishing-for-aws-credentials-via-aws-sso-device-code-authentication/)
    - So say we know tbe URL to the access portal... And we also obtained the username and password of a valid user...
        - We can then navigate to the access portal URL and login
        - After login, we see all the "permission sets" that are assigned to our user (these define the level of access)
    - What to do now?
        - First, we need to finde the region where our AWS IAM Identity Center was created 
            - For this, we run `curl https://d-xxxxxxxxxx.awsapps.com/start/ -s | grep -o '"region":"[^"]*"'`
        - Now, in the AWS Management Console, we set the region to that region
        - Now is a good moment to figure out what our user's permissions likely allow them to do
            - Usually, we may be able to infer this from the permission name
            - For example, `IdentityCenterReader` may hint that we can do stuff with the `IAM Identity Center` and we would navigate to this in the Management Console
    - Pulling off the Phishing Attack
        - Within the `IAM Identity Center`, we navigate to `Users` and check out what other users exist
            - We can click on the users to see things like their email address, their job title, etc.
        - Once we have identified a user we want to phish, we use `aws-sso-device-code-authentication` (https://github.com/christophetd/aws-sso-device-code-authentication), and run:
            - `python3 main.py -u https://d-xxxxxxxxxx.awsapps.com/start -r us-east-1  -o /tmp/token`
            - This outputs a `Device code URL`, which we send to the email of the victim
            - If the victim clicks on the link, and clicks through a few prompts, we get their AWS credentials!