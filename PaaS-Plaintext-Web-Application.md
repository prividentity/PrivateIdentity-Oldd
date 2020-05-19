## Setup PaaS plaintext web application ##

## Clone project ##
    
    `git clone git@github.com:openinfer/pb-web.git`

### Setup Environment variables ###

    cd $HOME/pb-web/kubernetes/aws/deployment
    cp variables.sh variables-test.sh  
    vi variables-test.sh

Note: Here **test ** is your cluster name. Please replace Frontend, Backend URL as per your requirements in variables-test.sh 
eg. export FRONTEND=test.private.id
    export BACKEND=dev.private.id

### Run Cluster command ###

    cd $HOME/pb-web/kubernetes/aws/
    . ./cluster-run.sh

Note: This command will build docker image and put that docker image into kubernetes cluster and you will be able to use Frontend URL to access it.