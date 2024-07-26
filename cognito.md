# Cognito

- `aws cognito-idp get-user --access-token <jwt>` - get the user’s information using their access token
- `aws cognito-idp initiate-auth` - login
- `aws cognito-idp sign-up` - create a new user (needs `--client-id` which can usually be founted somewhere in the globally accessible config or in JavaScript)
    - Example: `aws cognito-idp sign-up  --client-id <clientId> --username bobby --password Password123! --user-attributes Name="email",Value="your@email.com"`
    - Afterwards, the user needs to be confirmed via `confirm-sign-up`:
        - Example: `aws cognito-idp confirm-sign-up --region eu-central-1 --client-id <clientId> --username bobby --confirmation-code <code-received-via-email>`
- `aws cognito-identity get-id` - get the identity Id of the user (required for the next command)
    - Use the `Identity Token` (not the normal access token!) and pass it in via `--logins '{"https://cognito-idp.<region>.amazonaws.com/<user-pool-id>": "<token>"}'`
- `aws cognito-identity get-credentials-for-identity` (get temporary AWS creds for the user)
- `aws cognito-idp --region eu-central-1 update-user-attributes --access-token <token> --user-attributes Name='Email',Value='bobby@gmail.com'` (update a user's attributes in Cognito)