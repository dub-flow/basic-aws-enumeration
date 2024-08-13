# IAM Role

- `aws iam list-role-policies --role-name <role>` (list inline policies)
- `aws iam get-role-policy` (get statements of an inline policy)
- `aws iam list-attached-role-policies --role-name <role>` (list managed policies)
- `aws iam get-policy` (get current version of a managed policy) -> `get-policy` only looks for managed policies
- `aws iam get-policy-version` (get statements of the policy)