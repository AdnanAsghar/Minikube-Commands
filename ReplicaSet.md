## ReplicaSet
Create a yaml file named "rs.yaml"
```
$ cat rs.yaml
```
##### Result
```
kind: ReplicaSet
apiVersion: apps/v1
metadata: 
  name: myrs
spec:
  replicas: 3
  selector:
    matchLabels: 
      app: rsexample
  template: 
    metadata: 
      labels: 
        app: rsexample
    spec: 
      containers:
      - name: rscontainer
        image: aamirpinger/helloworld:latest
        ports:
        - containerPort: 80
```

```
$ kubectl create -f rs.yaml 
```
##### Result
```
replicaset.apps/myrs created
```

```
$ kubectl get po
```
##### Result
```
NAME         READY   STATUS    RESTARTS   AGE
myrs-g8nc4   1/1     Running   0          5m20s
myrs-hpx6d   1/1     Running   0          5m20s
myrs-nrz64   1/1     Running   0          5m20s
```
Get replica sets
```
$ kubectl get rs
```
##### Result
```
NAME   DESIRED   CURRENT   READY   AGE
myrs   3         3         3       6m
```

check pods with labels

```
$ kubectl get po --show-labels
```
##### Result
```
NAME         READY   STATUS    RESTARTS   AGE    LABELS
myrs-g8nc4   1/1     Running   0          7m8s   app=rsexample
myrs-hpx6d   1/1     Running   0          7m8s   app=rsexample
myrs-nrz64   1/1     Running   0          7m8s   app=rsexample
```

Get multiple resources in a single command
```
$ kubectl get rs,po,ns
```
##### Result
```
NAME                   DESIRED   CURRENT   READY   AGE
replicaset.apps/myrs   3         3         3       9m49s

NAME             READY   STATUS    RESTARTS   AGE
pod/myrs-g8nc4   1/1     Running   0          9m49s
pod/myrs-hpx6d   1/1     Running   0          9m49s
pod/myrs-nrz64   1/1     Running   0          9m49s

NAME                        STATUS   AGE
namespace/default           Active   10d
namespace/kube-node-lease   Active   10d
namespace/kube-public       Active   10d
namespace/kube-system       Active   10d
namespace/production        Active   123m
```

## Deleting ReplicaSet without pods
```
$ kubectl delete rs myrs --cascade=false
```
##### Result
```
replicaset.apps "myrs" deleted
```

## Deleting Pods and ReplicaSet
```
kubectl delete rs myrs
```
##### Result
```
replicaset.apps "myrs" deleted
```

## Operators in MatchExpressions
* In
* notIn
* Exists
* DoesNotExist


## Replica set with MatchExpressions
```
kind: ReplicaSet
apiVersion: apps/v1
metadata: 
  name: myrs
spec:
  replicas: 3
  selector:
    matchExpressions: 
    - key: app
      operator: In
      values:
      - rsexample
  template: 
    metadata: 
      labels: 
        app: rsexample
    spec: 
      containers:
      - name: rscontainer
        image: aamirpinger/helloworld:latest
        ports:
        - containerPort: 80
```

## Modifying ReplicaSet
```
$ cat rs.yaml 
```
##### Result
```
kind: ReplicaSet
apiVersion: apps/v1
metadata: 
  name: myrs
spec:
  replicas: 3
  selector:
    matchExpressions: 
    - key: app
      operator: In
      values:
      - rsexample
  template: 
    metadata: 
      labels: 
        app: rsexample
    spec: 
      containers:
      - name: rscontainer
        image: aamirpinger/helloworld:latest
        ports:
        - containerPort: 80
```

Edit already created ReplicaSet using ```$ kubectl edit rs myrs``` in vim editor and change the replicas to 5 from 3

```
$ kubectl get po,rs
```

##### Result
```
NAME             READY   STATUS              RESTARTS   AGE
pod/myrs-4ktgh   1/1     Running             0          8m42s
pod/myrs-kkbd2   1/1     Running             0          8m42s
pod/myrs-nm84l   1/1     Running             0          5s
pod/myrs-pjlm9   0/1     ContainerCreating   0          5s
pod/myrs-zjr86   1/1     Running             0          8m42s

NAME                   DESIRED   CURRENT   READY   AGE
replicaset.apps/myrs   5         5         4       8m42s
```

```
$ cat rs.yaml 
```

```
kind: ReplicaSet
apiVersion: apps/v1
metadata: 
  name: myrs
spec:
  replicas: 5
  selector:
    matchExpressions: 
    - key: app
      operator: In
      values:
      - rsexample
  template: 
    metadata: 
      labels: 
        app: rsexample
    spec: 
      containers:
      - name: rscontainer
        image: aamirpinger/helloworld:latest
        ports:
        - containerPort: 80
```


## Scaling ReplicaSet
```
$ kubectl scale rs myrs --replicas=3
```
##### Result
```
replicaset.apps/myrs scaled
```

```
$ kubectl get po,rs
```

##### Result
```NAME             READY   STATUS    RESTARTS   AGE
pod/myrs-4ktgh   1/1     Running   0          14m
pod/myrs-kkbd2   1/1     Running   0          14m
pod/myrs-zjr86   1/1     Running   0          14m

NAME                   DESIRED   CURRENT   READY   AGE
replicaset.apps/myrs   3         3         3       14m
```
