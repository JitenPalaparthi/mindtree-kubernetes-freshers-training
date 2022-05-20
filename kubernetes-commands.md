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

  - To know more information about pod
    - ```kubectl describe pod nginx -n dev```