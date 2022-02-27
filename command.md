# KUBERNETES

## COMMAND

### KUBECTL
    kubectl get nodes
    kubectl get nodes 'name'
    kubectl describe nodes
    kubectl describe nodes 'name'
    kubectl get po -A
    kubectl describe po -n 'namespace' 'name-pod'
    kubectl get po -A -o wide
    kubectl get po -n 'namespace' 'name-pod' -o yaml
    kubectl run 'name-pod' --image='image-container' --port='port-container'
    kubectl create -f '.yaml'
    kubectl apply -f '.yaml'
    kubectl expose po 'name-pod'
    kubectl expose po nginx --port=80
    kubectl expose deployment 'name-deployment'
    kubectl edit service 'name-service'
    kubectl explain po | svc | ...
    kubectl get po,svc,endpoints
    kubectl get all
    kubectl scale --replicas='number' deployment 'name-deployment'
    kubectl explain pod
