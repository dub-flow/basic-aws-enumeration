# IAM General

- `aws iam create-access-key --user-name <username>` - generate an access key
    - If we don't know our username, e.g. if we took over an `assumed role` e.g. via the device code phishing attack, then we can run `aws iam list-users` and try to infer which username might be ours