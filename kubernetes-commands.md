# Kubernetes

## minikube 

```minikube version```

- To start minikube

```minikube start```

- To start minikube with 3 nodes

```minikube start -n 3```

## Basic Commands

```kubectl cluster-info```

```kubectl cluster-info dump```

- To know all resources in kubernetes
- ```kubectl api-resources```

- Create a namespace

```kubectl create namespace dev```

- To list all namespaces

```kubectl get ns```

- Pod
  - List pods from all namespaces
   ```kubectl get pods -A```
   - List pods from specific namespace
   - ```kubectl get pods -n kube-system```
  - Create a pod
    - There are two ways to create a pod
    - 1- Through command line.
      - Create a pod called nginx , port 80 in dev namespace
      - ```kubectl run nginx --image=nginx --port=80 -n dev```
    - 2- Through manifest file
      - Here is the manifest file of [nginx pod](workloads/create-nginx-pod.yaml)
      - To create pod from the manifest file use the below command
      - ```kubectl create -f workloads/create-nginx-pod.yaml -n dev```
  - To know more information about pod
    - ```kubectl describe pod nginx -n dev```
  - To exec into the pod/container
  - ```kubectl exec -it nginx -c nginx -n dev bash```
  - To fetch logs from a pod
  - ```kubectl logs nginx -n dev```
  - To fetch logs from a pod , follow logs
  - ```kubectl logs -f nginx -n dev```
  - To fetch logs from a pod tailered logs. This gives last 5 logs
  - ```kubectl logs --tail=5 nginx -n dev```
  - To delete a pod
  - ```kubectl delete pod nginx -n dev```
  - Service
    - ```kubectl create -f workloads/create-nginx-service.yaml -n dev```
    - There are three types to access the servce
    - type: ClusterIP
      - ClusterIP type is used to access only inside the cluster
    - type: NodePort
      - NodePort type is used to access only through node ip address
    - type: LoadBalancer
      - LoadBalancer type is used to access through the cloud provider load balancer ip
  - Deployment
    - Deployments are used to run more replicas. They can scale up or down based on the load
    - Delete the nginx pod before running the deployment. If service is already runnign no need to resum the service.
    - ```kubectl create -f workloads/create-nginx-deployment.yaml -n dev```
    - Scale the deployment up/down. Up is giving more numbers and down is giving less number
    - ```kubectl scale --replicas=10 deployment nginx -n dev```
    - Scale up/down can also be done through the deployment file, change replicas: property value
    - ```kubectl edit deployment nginx -n dev```

