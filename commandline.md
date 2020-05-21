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
## Replica Controller
'''ssh
$ kubectl create -f rc-definition.yml
$ kubectl get replicationcontroller
$ kubectl get pods

'''

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
```
