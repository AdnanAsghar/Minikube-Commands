## Job
```
$ cat job.yaml
```
##### Result
```
kind: Job
apiVersion: batch/v1
metadata:
  name: jobexample
spec: 
  template:
    spec: 
      containers:
      - name: jobcontainer
        image: docker/whalesay
        command: ["cowsay","This is job resourse example"]
    restartPolicy: Never
  backoffLimit: 4
  activeDeadlineSeconds: 60
```
```
$ kubectl create -f job.yaml 
```
```
job.batch/jobexample created
```
```
$ kubectl get job
```
```
NAME         COMPLETIONS   DURATION   AGE
jobexample   0/1           46s        46s
```

```
$ kubectl get po
```
```
NAME               READY   STATUS              RESTARTS   AGE
jobexample-9mcrs   0/1     ContainerCreating   0          50s
myrs-4ktgh         1/1     Running             0          31m
myrs-kkbd2         1/1     Running             0          31m
myrs-zjr86         1/1     Running             0          31m
```
```
$ kubectl logs jobexample-9mcrs
```
```

 ______________________________ 
< This is job resourse example >
 ------------------------------ 
    \
     \
      \     
                    ##        .            
              ## ## ##       ==            
           ## ## ## ##      ===            
       /""""""""""""""""___/ ===        
  ~~~ {~~ ~~~~ ~~~ ~~~~ ~~ ~ /  ===- ~~~   
       \______ o          __/            
        \    \        __/             
          \____\______/   
```
