## Run Spark on EMR with Scripts 

- [ref](http://aws.amazon.com/articles/4926593393724923)

### Install Client Command Terminal
- If you haven't install pip
  - [ref](http://www.cyberciti.biz/faq/debian-ubuntu-centos-rhel-linux-install-pipclient/)
  ```
  yum -y install python-pip
  $ echo 'alias pip="/usr/bin/pip-python"' >> $HOME/.bashrc
  $ . $HOME/.bashrc
  ```
- Install `awscli`
  - command: `pip install awscli`
  
### Create User and Download Access Key and Value
- [ref](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html#cli-signup)
- Steps
  1. In `IAM` console, on the left column, create user
  2. Download crendentials, or copy down the `Access Key Id` and `Secret Access Key`
  3. Attach user with policy, such as `AdministratorAccess`
  
  
### Configure awscli
- Configure awscli by editing the files
  1. create file `~/.aws/config`
   ```
  [default]
  region=xx
  output=json
  ```
   2. create file `~/.aws/credentials`
  ```
  [default]
  aws_access_key_id=xx
  aws_secret_access_key=xx
  ```
  
  
### Create Other Users (Optional)
- Note only if you have already by an user and has attached with policies will you be able to create other users, which means the first user cannot be created using awscli.
- attach policy
```
aws iam attach-user-policy --user-name created-by-cli --policy-arn arn:aws:iam::aws:policy/AdministratorAccess
```

### Create Roles
- Create default roles using the following command
```
aws emr create-default-roles
```
- After created roles, the file `~/.aws/config` will become
```
  [default]
region=xx
output=json
emr =
    service_role = EMR_DefaultRole
    instance_profile = EMR_EC2_DefaultRole
```

### Create EC2 Key
- [ref](http://docs.aws.amazon.com/cli/latest/userguide/cli-ec2-keypairs.html)
- You must specify a key pair when you launch and connect to an Amazon EC2 instance.
```
aws ec2 create-key-pair --key-name my-ec2-key --query 'KeyMaterial' --output text > /workspace/amazon/my-key.pem
```
- Change permission: If you're using an SSH client on a Linux computer to connect to your instance, use the following command to set the permissions of your private key file so that only you can read it.
```
 chmod 400 my-key.pem
```

### Create Cluster
- command
```
aws emr create-cluster --name xx --ami-version 3.2 --instance-type m3.xlarge --instance-count 3 --ec2-attributes KeyName=my-key --bootstrap-actions Path=s3://support.elasticmapreduce/spark/install-spark
```
- Returned
```
"ClusterId": "j-xx"
```


### Connect to Cluster
```
aws emr ssh --cluster-id j-xx --key-pair-file my-key.pem 
```
