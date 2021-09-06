# useful

Get region in AWS from EC2

REGION=$(/usr/bin/curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone | sed 's/[a-z]$//')

Get a parameter from SSM Parameter store

DB_PASSWORD=$(aws ssm get-parameter --name $SSM_DB_PASSWORD --query Parameter.Value --with-decryption --region $REGION --output text)

Get a EFS id by Name

EFS_ID=$(aws efs describe-file-systems --query 'FileSystems[?Name==`gh_data`].FileSystemId' --region $REGION --output text)
