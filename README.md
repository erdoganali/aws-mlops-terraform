# aws-mlops-terraform
using Terraform AWS provider, deploy Fastapi app which is importing the ml model from S3 bucket and insert prediction to RDS Mysql

terraform init

terraform validate

terraform plan

terraform apply --auto-approve

terraform destroy --auto-approve

terraform destroy -target=aws_instance.mlops_dev_node

ssh-keygen -t rsa -b 2048 -f ~/.ssh/mlops-central-key

ssh-keygen -t rsa -b 2048 -f ~/.ssh/mlops-central-key -N ''

resource "aws_key_pair" "mlops_auth" { public_key = file("~/.ssh/mlops-central-key.pub") key_name = "mlops-aws-key" }

export DATABASE_URL="mysql+pymysql://mlops_user:Ankara06@mlops-db.cw17zk3pwfhh.eu-west-1.rds.amazonaws.com/mlops-db"

source /fastapi/bin/activate

uvicorn main:app --host 0.0.0.0 --port 8000 --reload --log-level debug

sudo systemctl status uvicorn

ssh -i "mlkey.pem" ec2-user@ec2-3-67-132-170.eu-central-1.compute.amazonaws.com
