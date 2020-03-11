### Delete Cluster and stack

#### Follow bellow command to delete Cluster, mysql and redis.
      cd $HOME/pb/kubernetes/deployment
      ./delete_all.sh

   [images/stack1.png]

Note: This command will delete complete EKS including mysql and redis stack. Make sure you have correct parameters in variables.sh and mysql-redis-variables.sh Because this script uses parameters from mysql-redis-variables.sh and variables.sh scripts.
 
#### To delete Mysql stack
     cd $HOME/pb/kubernetes/deployment
     ./delete_mysql_stack.sh 

Note: This script will delete mysql stack from aws. It uses parameters from mysql-redis-variables.sh make sure it have correct values. 

### To delete Redis Stack
     cd $HOME/pb/kubernetes/deployment
     ./delete_redis_stack.sh

Note: This script will delete redis stack from aws. It uses parameters from mysql-redis-variables.sh make sure it have correct values.