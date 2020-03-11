### Delete Cluster and stack

#### Follow bellow command to delete Cluster, mysql and redis.
      cd $HOME/pb/kubernetes/deployment
      ./delete_all.sh

Note: This command will delete complete EKS including mysql and redis stack. Make sure you have correct parameters in variables.sh and mysql-redis-variables.sh Because this script uses parameters from mysql-redis-variables.sh and variables.sh scripts.

[[images/stack2.png]]
[[images/stack1.png]]

 
#### To delete Mysql stack
     cd $HOME/pb/kubernetes/deployment
     ./delete_mysql_stack.sh 

Note: This script will delete mysql stack from aws. It uses parameters from mysql-redis-variables.sh make sure it have correct values. 

[[images/stack3.png]]

### To delete Redis Stack
     cd $HOME/pb/kubernetes/deployment
     ./delete_redis_stack.sh

Note: This script will delete redis stack from aws. It uses parameters from mysql-redis-variables.sh make sure it have correct values.

[[images/stack4.png]]