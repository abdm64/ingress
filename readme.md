## 📝 Table of Contents

- [About](#about)
- [Getting Started](#getting_started)
- [installing kubectl cammand line](#kubectl)
- [helm ](#helm)
- [installing ingress nginx controller using helm ](#deployment)
- [Testing the ingress nginx ](#test)
- [uninstall  ingress nginx ](#remove)



## 🧐 About <a name = "about"></a>

- add whatever you want ( but i suggest that you check the ingress nginx documentation )


## 🏁 Getting Started <a name = "getting_started"></a>

These instructions will help you setup ingress nginx on you kubernetes cluster you must have acess to kubernetes cluster and have kubectl and helm insstaled on your machine .


### Prerequisites

You need to install the fellowing software in order to get the ingress nginx  up and running :

- Helm.
- kubectl .

## installing kubectl  <a name = "kubectl"></a>

- Download the latest release with the command: 


```
curl -LO "https://dl.k8s.io/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl.sha256" 

```

- Install kubectl : 

```
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

```

- Test to ensure the version you installed is up-to-date:


```
kubectl version --client

```

## installing Helm Kubernetes packege ma  <a name = "helm"></a>

- Download the latest release with the command: 


```
 curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3
```

- Give it the right acess : 

```
chmod 700 get_helm.sh

```
- install helm 

```
./get_helm.sh

```

- Test to ensure the version you installed is up-to-date:


```
helm  -- help 

```

## 🏁 installing ingress nginx controller using helm <a name = "deployment"></a>


to install ingress nginx on your kubernetes cluster with helm you just need to run the fellowing cammands :

- first you need to create namespace that hold all the related ingress resources : 

```
kubectl create ns ingress-nginx

```
- second add the the ingress nginx repo  : 

```
helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx

```
- update your repos 

```
helm repo update

```

- install ingress nginx  with the default params 

```
helm install ingress-nginx ingress-nginx/ingress-nginx -n ingress-nginx

```

to checke the installation of ingress nginx run the fellowing : 

```
kubectl get all  -n ingress-nginx

```

that should return the realted resources


##  Testing the ingress nginx <a name = "test"></a>

you can find the k8s folder attached to this article that have resource for  simple web api deployment  to test if the ingress is working  just run the fellowing cammand : 


```
kubectl apply -f k8s

```

and now visit on  the browser on ip adress of the cluster (if you are n local you should use localhost)
you can see message "Hello World!"


to remove the deployment just run 


```
kubectl delete  -f k8s

```
##  uninstall  ingress nginx <a name = "remove"></a>

just run the cammand 

```
helm uninstall ingress-nginx

```







