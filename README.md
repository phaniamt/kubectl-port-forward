# kubectl-port-forward
### Port forward the db pod to local server 

### Mongodb pod names

    mongo-1-0  
    mongo-2-0 
    mongo-3-0

#### Get the service token ####

    kubectl get secret $(kubectl get serviceaccount developer -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode

### Example: Port forward from mongo-1-0

#### Run the below command in 10.0.1.1 as root user or sudo user

    kubectl port-forward --address 10.0.1.1 mongo-1-0   --namespace db 38030:27017 --kubeconfig=/root/config/kube-config.yaml
    
#### Screen commands.

##### Create the new screen

    screen -S mongo
    
###### Run the command then press CTRL+a+d for exit from screen

##### List the All screens

     screen -ls
     
##### Attach the screen

     screen -x mongo  
