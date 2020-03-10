## ElastiCache Redis
Amazon ElastiCache is a web service that makes it easy to set up, manage, and scale a distributed in-memory data store or cache environment in the cloud. It provides a high-performance, scalable, and cost-effective caching solution. At the same time, it helps remove the complexity associated with deploying and managing a distributed cache environment.

## RDS MYSQL 
Amazon RDS for MySQL is compliant with many industry standards. For example, you can use Amazon RDS for MySQL databases to build HIPAA-compliant applications and to store healthcare related information, including protected health information (PHI) under an executed Business Associate Agreement (BAA) with AWS

### prerequisites
1. AWS must be configured on your system
2. EKS cluster must be deployed

### Setup mysql and redis cluster
#### 1. Go to location and change variables for mysql and redis 
       cd $HOME/pb/kubernetes/deployment`
       vi mysql-redis-variables.sh`

#### 2. Deploy Clouformation templates for mysql and redis
       cd $HOME/pb/kubernetes/deployment
       . ./setup-mysql-redis.sh

Note: You can change cloudformation template if you want to add more parameters in it. Go to location $HOME/pb/kubernetes/deployment/cloudformation_template

#### 3. Wait for some time to complete stack deploy

### To delete Mysql stack
     aws cloudformation delete-stack --stack-name $MYSQL_STACK_NAME
### To delete Redis Stack
     aws cloudformation delete-stack --stack-name $REDIS_STACK_NAME