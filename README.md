

## Configure Dashboard

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml


Access via
    http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/


## Create Application
1. Run a Hello World application in your cluster: Create the application Deployment using the file above:

    kubectl apply -f hello-world.yaml

The preceding command creates a Deployment and an associated ReplicaSet. The ReplicaSet has two Pods each of which runs the Hello World application.

Display information about the Deployment:

    kubectl get deployments hello-world
    kubectl describe deployments hello-world

    kubectl get replicasets
    kubectl describe replicasets


## Create Service

    # kubectl expose deployment hello-world --type=NodePort --name=hello-world-service
    # kubectl expose deployment/hello-world --type="NodePort" --port 9000

    kubectl expose deployment hello-world --type=LoadBalancer --name=hello-world-service

    kubectl describe services hello-world-service

    kubectl get pods --selector="run=load-balancer-example" --output=wide

    kubectl cluster-info


    kubectl get services hello-world
    kubectl describe services hello-world

    $NODE_PORT=kubectl get services/hello-world -o go-template='{{(index .spec.ports 0).nodePort}}'


