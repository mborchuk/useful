# useful

Get region in AWS from EC2

REGION=$(/usr/bin/curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone | sed 's/[a-z]$//')

Get a parameter from SSM Parameter store

DB_PASSWORD=$(aws ssm get-parameter --name $SSM_DB_PASSWORD --query Parameter.Value --with-decryption --region $REGION --output text)

Get a EFS id by Name

EFS_ID=$(aws efs describe-file-systems --query 'FileSystems[?Name==`gh_data`].FileSystemId' --region $REGION --output text)


# Docker
## output logs inside containers
echo 'bla bla bla' >> /proc/1/fd/1

Examples:
echo '{"log.timestamp": "2022-11-20 18:20:02,856", "log.module": "Pythonbroker", "log.level": "DEBUG", "log.function": "on_message", "log.message": "on_message - finally - check_if_termination_is_required()"}' >> /proc/1/fd/1

echo '{"timestamp": "2022-11-20 18:20:02,856", "module": "Pythonbroker", "level": "DEBUG", "function": "on_message", "message": "on_message - finally - check_if_termination_is_required()"}' >> /proc/1/fd/1

echo '{}' >> /proc/1/fd/1