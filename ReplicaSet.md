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
