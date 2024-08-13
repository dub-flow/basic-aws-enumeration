# EC2

- `aws ec2 describe-instances --region us-east-1` - Find public IP and check for a web app
- `aws ec2 describe-volumes` - list EBS volumes
- `aws ec2 describe-snapshots` - list EBS snapshots

- Investigate an EBS Snapshot:
    - Run `dsnap --region us-east-2 list`: Shows us all snapshots
    - Run `dsnap --region us-east-2 get <snap_id>`: Download the snapshot
    - Mount an image using docker to checkout the filesystem: `sudo IMAGE=<path_to_snapshot> make docker/run`
        - `Note 1`: This command has to be ran from withint the `dnsap` folder (where the `Makefile` is)
        - `Note 2`: For some weird reason, we provide `<path_to_snapshot>` without the initial slash
            - So if the `snapshot` is in `/home/user/my.img`, then we provide `IMAGE=home/user/my.img`

- `aws ec2 describe-instance-attribute --instance-id <instance-id> --attribute userData --query "UserData.Value" --output text | base64 --decode` - get EC2 User Data
    - Alternatively, we can dump the User Data of all EC2 instance via the `EC2userdDataDumper.sh` (https://github.com/cloudbreach/CloudBreach_AWSScripts/blob/master/EC2userDataDumper.sh)

- Most interesting endpoints of IMDS:
    - http://169.254.169.254/latest/user-data -> get the user data script
    - http://169.254.169.254/latest/meta-data/iam -> get credentials for the IAM roles attached to the EC2 instance
    