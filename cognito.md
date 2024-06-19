# Cognito

- `aws cognito-idp get-user` - get the user’s information using their access token
- `aws cognito-idp initiate-auth` - login
- `aws cognito-idp sign-up` - create a new user
- `aws cognito-identity get-id` - get the identity Id of the user (required for the next command)
    - Use the `Identity Token` (not the normal access token!) and pass it in via `--logins '{"https://cognito-idp.<region>.amazonaws.com/<user-pool-id>": "<token>"}'`
- `aws cognito-identity get-credentials-for-identity` (get temporary AWS creds for the user)