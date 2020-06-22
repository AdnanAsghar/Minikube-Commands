```
$ cat cj.yaml 
```
```
kind: CronJob
apiVersion: batch/v1beta1
metadata: 
  name: cj
spec: 
  schedule: "* * * * *"
  jobTemplate: 
    spec: 
      template:
        metadata:
          labels:
            app: cjexample
        spec:
          containers:
          - name: cjcontainer
            image: docker/whalesay
            command: ["cowsay","Cronjob Example"]
          restartPolicy: Never
```
```
$ kubectl create -f cj.yaml 
```
```
cronjob.batch/cj created
```

```
$ kubectl get cj
```
```
NAME   SCHEDULE    SUSPEND   ACTIVE   LAST SCHEDULE   AGE
cj     * * * * *   False     0        23s             105s
```

```
$ kubectl get cj,job,pod
```
```
NAME               SCHEDULE    SUSPEND   ACTIVE   LAST SCHEDULE   AGE
cronjob.batch/cj   * * * * *   False     1        7s              2m29s

NAME                      COMPLETIONS   DURATION   AGE
job.batch/cj-1592767140   1/1           11s        2m4s
job.batch/cj-1592767200   1/1           5s         64s
job.batch/cj-1592767260   0/1           4s         4s
job.batch/jobexample      1/1           6s         77m

NAME                      READY   STATUS              RESTARTS   AGE
pod/cj-1592767140-klfp2   0/1     Completed           0          2m4s
pod/cj-1592767200-4xctt   0/1     Completed           0          64s
pod/cj-1592767260-cv2zg   0/1     ContainerCreating   0          4s
pod/jobexample-g6dbs      0/1     Completed           0          77m
pod/myrs-4ktgh            1/1     Running             0          3h9m
pod/myrs-kkbd2            1/1     Running             0          3h9m
pod/myrs-zjr86            1/1     Running             0          3h9m
```

```
$ kubectl logs cj-1592767260-cv2zg
```

```
 _________________ 
< Cronjob Example >
 ----------------- 
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

Deleting CJ will remove all its job and pods
```
$ kubectl delete cronjob cj
```
```
cronjob.batch "cj" deleted
```

```
$ kubectl get cj,job,pod
```
```
NAME                   COMPLETIONS   DURATION   AGE
job.batch/jobexample   1/1           6s         80m

NAME                   READY   STATUS      RESTARTS   AGE
pod/jobexample-g6dbs   0/1     Completed   0          80m
pod/myrs-4ktgh         1/1     Running     0          3h13m
pod/myrs-kkbd2         1/1     Running     0          3h13m
pod/myrs-zjr86         1/1     Running     0          3h13m
```
