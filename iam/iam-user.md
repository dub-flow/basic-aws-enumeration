# IAM User

- `aws sts get-caller-identity` (whoami?)
- `aws iam get-user --user-name <breached_user>` (get user information, including permission boundaries, password last used, etc.)
- `aws iam list-groups-for-user` (what groups am I a part of?)
- `aws iam list-group-policies` (what policies are attached to those groups?)
- `aws iam get-policy` (what statements compose these policies?) -> `get-policy` only looks for managed policies
- `aws iam get-policy-version` (what statements compose these policies?)
- `aws iam list-user-policies --user-name <breached_user>` (what are the inline policies for this user?)
- `aws iam get-user-policy --user-name <breached_user> --policy-name <policyname>` (what statements compose these policies?) -> `get-user-policy` looks for inline policies 
- `aws iam list-attached-user-policies --user-name <breached_user>` (what policies are attached to this user?)
    - We run `iam get-policy` again to access the version of the policy
    - Last, we run `iam get-policy-version` to get access to the statements