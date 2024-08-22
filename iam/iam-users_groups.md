# IAM Users and Groups

* Enumerating a User:
    - `aws sts get-caller-identity` (whoami?)
    - `aws iam get-user --user-name <breached_user>` (get user information, including permission boundaries, password last used, etc.)
    - `aws iam list-groups-for-user --user-name <breached_user>` (what groups am I a part of?)
        - If we find the user to be in a group, we can continue with the `Enumerating a Group` section (see below)
    - `aws iam list-user-policies --user-name <breached_user>` (what are the inline policies for this user?)
        - `aws iam get-user-policy --user-name <breached_user> --policy-name <policyname>` (what statements compose these policies?) -> `get-user-policy` looks for inline policies 
    - `aws iam list-attached-user-policies --user-name <breached_user>` (what policies are attached to this user?)
        - We run `aws iam get-policy --policy-arn <arn>` again to access the version of the policy
        - Last, we run `aws iam get-policy-version  --policy-arn <arn> --version-id <version>` to get access to the statements

* Enumerating a Group:
    - `aws iam list-group-policies --group-name <group>` (what inline policies does the group have?)
        - `aws iam get-group-policy --group-name <group> --policy-name <policyname>` (what statements does this inline policy have these policies?)
    - `aws iam list-attached-group-policies --group-name <group>` (what attached policies does the group have?)
        - Now we again run `get-policy` and then `get-policy-version` (same as above with attached user policies)
