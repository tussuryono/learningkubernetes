## Pods
Checking jumlah pod yang aktif / verifikasi creating pod
```ssh
$ kubectl get pods
```

Create pod
```ssh
$ kubectl run nginx --image=nginx --generator=run-pod/v1
```

Detail pod
```ssh
$ kubectl get pods -o wide
```

Deskripsi pod
```ssh
$ kubectl describe pod nginx
```

Menghapus pod
```ssh
$ kubectl delete pod nginx
```

create pod menggunakan yaml file
```ssh
$ kubectl create -f 01-nginx-pod-definition.yaml
```

Implementasi hasil editing file yaml
```ssh
$ kubectl apply -f 01-nginx-pod-definition.yaml
```

Untuk editing direct bisa menngunakan command
```ssh
$ kubectl edit pod nginx
```

Delete pod
```ssh
$ kubectl delete pod redis-pod
```

listing pod dari namespace yang berbeda
```ssh
$ kubectl get pods --namespace=kube-system
$ kubectl create pod pod-definition.yaml --namespace=dev
```

```ssh
$ kubectl run --generator=run-pod/v1 nginx --image=nginx --dry-run -o yaml
$ kubectl run --generator=run-pod/v1 nginx-pod --image=nginx:alpine

$ kubectl run --generator=run-pod/v1 redis --image=redis:alpine -l tier=db
$ kubectl expose pod redis --port=6379 --name=redis-service

$ kubectl create deployment webapp --image=kodekloud/webapp-color
$ kubectl scale deployment/webapp --replicas=3
```


## Replica Controller
```ssh
$ kubectl create -f rc-definition.yml
$ kubectl get replicationcontroller
$ kubectl get pods

```

## Replica Sets
```ssh
$ kubectl create -f 01-nginx-replicaset-definition.yml
$ kubectl get replicaset
$ kubectl describe replicaset myapp-replicaset

$ kubectl replace -f 01-nginx-replicaset-definition.yml
$ kubectl scale --replicas=6 -f 01-nginx-replicaset-definiiton.yml
$ kubectl scale --replicas=6 replicaset myapp-replicaset

$ kubectl delete replicaset myapp-replicaset
```

## Deployment
```ssh
$ kubectl create -f 01-nginx-deployment-definition.yaml
$ kubectl get deployments
$ kubectl get replicaset
$ kubectl get pods

$ kubectl get all


$ kubectl describe deployments.apps fronted-deployment | grep -i image
$ kubectl apply -f deployment-definition.yaml

$ kubectl create deployment httpd-frontend --image=httpd:2.4-alpine
$ kubectl scale deployment httpd-frontend --replicas=3

$ kubectl expose deployment simple-webapp-deployment --type=NodePort --target-port=8080 --target-port=8080 --name=webapp-service --dry-run -o yaml > svc.yaml

$ kubectl create deployment --image=nginx nginx --dry-run -o yaml
$ kubectl create deployment --image=nginx nginx --dry-run -o yaml > nginx-deployment.yaml
```

## Namespace
```ssh
$ kubectl create -f namespace-dev-definition.yaml
or
$ kubectl create namespace dev
$ kubectl get namespace
$ kubectl get namespace --no-headers | wc -l
$ kubectl get pods --namespace=dev
$ kubectl -n <namespace> get pods
$ kubectl run redis --image=redis --restart=Never --dry-run -o yaml > pod.yaml

merubah namespace default menjadi dev
$ kubectl config set-context $(kubectl config current-context) --namespace=dev

listing all pods untuk seluruh all namespace
$ kubectl get pods --all-namespaces
$ kubectl get pods --all-namespaces | grep -i blue

Limit quota setting
$ kubectl create -f compute-quota.yaml 

creating pod using namespace setting
$ kubectl run redis --image=nginx --generator=run-pod/v1 --namespace=finance
$ kubectl delete pod redis --namespace=finance


```

## Services
```ssh
$ kubectl create -f service-definition.yaml
$ kubectl get services

check dari command line user 
$ curl http://192.168.1.2:3008
```

## Service IP Cluster
```ssh
$ kubectl create -f service-ipcluster-definition.yaml
$ kubectl get services
$ kubectl get services --all-namespaces
$ kubectl describe service kubernetes
```
