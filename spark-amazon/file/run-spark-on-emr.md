## Run Spark On EMR

- [Ref](http://aws.amazon.com/articles/4926593393724923)

### Install Client Command Terminal
- If you haven't install pip
  - [ref](http://www.cyberciti.biz/faq/debian-ubuntu-centos-rhel-linux-install-pipclient/)
  ```
  yum -y install python-pip
  ```
- Install `awscli`
  - command: `pip install awscli`
  
### Get access key ID and secret access key
- [ref](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html#cli-signup)
- Keys
```
Access Key ID: xxxxx
Secret Access Key: xxxxx
```

### Create EC2 key-value pair
- [ref](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)
- set permission to read
```
chmod 400 my-key-pair.pem
```

### Attach Policy
- I select  `AdministratorAccess`

### Configure AWS
- [ref](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-started.html)
- create configure file in `~/.aws/config` and `~/.aws/credentials` respectively
  ```
  mkdir ~/.aws
  ```
- Create `~/.aws/config` as
```
[default]
region=xxx
output=json
```
- Create `~/.aws/crendentials` as
```
 [default]
aws_access_key_id=xxxx
aws_secret_access_key=xxxx
```

### Create Spark Cluster
- Create cluster
  - Command
   ```
  aws emr create-cluster --name xxx --ami-version 3.2 --instance-type m3.xlarge --instance-count 3 --ec2-attributes KeyName=xx --application Name=Hive --bootstrap-actions Path=s3://support.elasticmapreduce/spark/install-spark
  ```
  - Results
  ```
  "ClusterId": "j-xx"
  ```
  - Check Cluster Status
  - `aws emr describe-cluster --cluster-id j-xx`
  
### Connect to cluster
- Approach 1: assh to master node
  ```
  ssh hadoop@dns -i xx.pem 
  ```
- Approach 2: ssh with cli
  ```
  aws emr ssh --cluster-id j-xx --key-pair-file ~/mykeypair.key
  ```
