# Replica Sets
```ssh
$ kubectl create -f 01-nginx-replicaset-definition.yml
$ kubectl get replicaset

$ kubectl replace -f 01-nginx-replicaset-definition.yml
$ kubectl scale --replicas=6 -f 01-nginx-replicaset-definiiton.yml
$ kubectl scale --replicas=6 replicaset myapp-replicaset

$ kubectl delete replicaset myapp-replicaset
```
