### Backdoors

#### Reset Server

#### Step 1 : Access the pod name for the pb-app by running the following command
              kubectl get pods

#### Step 2 : Run the following command to access into the bash of the current pb-app pod
              kubectl exec -it <pod-name> bash

#### Step 3: Execute the following commands to reset the server
             cd $HOME/pb
             git pull
             cd $HOME/pb/kubernetes/code/pbapp/aws
             . ./variables.sh
             cd $HOME/pb/TrueID/src/bash/reset.sh
             . ./reset.sh