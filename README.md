# Minikube-Commands

## Start minikude
```
$ minikube start
```
##### Result
```
😄  minikube v1.11.0 on Darwin 10.15.5
✨  Using the hyperkit driver based on existing profile
👍  Starting control plane node minikube in cluster minikube
🔄  Restarting existing hyperkit VM for "minikube" ...
🐳  Preparing Kubernetes v1.18.3 on Docker 19.03.8 ...
🔎  Verifying Kubernetes components...
🌟  Enabled addons: default-storageclass, storage-provisioner
🏄  Done! kubectl is now configured to use "minikube"
```

## Check minikube Status
```
$ minikube status
```
##### Result
```
minikube
type: Control Plane
host: Running
kubelet: Running
apiserver: Running
kubeconfig: Configured
```

## Check cluster info

```
$ kubectl cluster-info
```
##### Result
```
Kubernetes master is running at https://192.168.64.3:8443
KubeDNS is running at https://192.168.64.3:8443/api/v1/namespaces/kube-system/services/kube-dns:dns/proxy

To further debug and diagnose cluster problems, use 'kubectl cluster-info dump'.
```

## Get Nodes
```
$ kubectl get nodes
or
$ kubectl get nodes
```
##### Result
```
NAME       STATUS   ROLES    AGE   VERSION
minikube   Ready    master   8d    v1.18.3
```

## Get Description of all Nodes 
```
$ kubectl describe nodes
or
$ kubectl describe no
```
##### Result
```
Name:               minikube
Roles:              master
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/os=linux
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=minikube
                    kubernetes.io/os=linux
                    minikube.k8s.io/commit=57e2f55f47effe9ce396cea42a1e0eb4f611ebbd
                    minikube.k8s.io/name=minikube
                    minikube.k8s.io/updated_at=2020_06_11T19_02_35_0700
                    minikube.k8s.io/version=v1.11.0
                    node-role.kubernetes.io/master=
Annotations:        kubeadm.alpha.kubernetes.io/cri-socket: /var/run/dockershim.sock
                    node.alpha.kubernetes.io/ttl: 0
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Thu, 11 Jun 2020 19:02:32 +0500
Taints:             <none>
Unschedulable:      false
Lease:
  HolderIdentity:  minikube
  AcquireTime:     <unset>
  RenewTime:       Sat, 20 Jun 2020 18:55:18 +0500
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Sat, 20 Jun 2020 18:54:39 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Sat, 20 Jun 2020 18:54:39 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Sat, 20 Jun 2020 18:54:39 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Sat, 20 Jun 2020 18:54:39 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:  192.168.64.3
  Hostname:    minikube
Capacity:
  cpu:                2
  ephemeral-storage:  16954224Ki
  hugepages-2Mi:      0
  memory:             3936940Ki
  pods:               110
Allocatable:
  cpu:                2
  ephemeral-storage:  16954224Ki
  hugepages-2Mi:      0
  memory:             3936940Ki
  pods:               110
System Info:
  Machine ID:                 1407419cbe9e450887ca56f2c66dd91b
  System UUID:                13a811ea-0000-0000-b7da-acbc32793da9
  Boot ID:                    4dbb55d1-58af-44aa-ac1b-8d68ef5e9d9e
  Kernel Version:             4.19.107
  OS Image:                   Buildroot 2019.02.10
  Operating System:           linux
  Architecture:               amd64
  Container Runtime Version:  docker://19.3.8
  Kubelet Version:            v1.18.3
  Kube-Proxy Version:         v1.18.3
Non-terminated Pods:          (8 in total)
  Namespace                   Name                                CPU Requests  CPU Limits  Memory Requests  Memory Limits  AGE
  ---------                   ----                                ------------  ----------  ---------------  -------------  ---
  kube-system                 coredns-66bff467f8-hvbrm            100m (5%)     0 (0%)      70Mi (1%)        170Mi (4%)     8d
  kube-system                 coredns-66bff467f8-j6x25            100m (5%)     0 (0%)      70Mi (1%)        170Mi (4%)     8d
  kube-system                 etcd-minikube                       0 (0%)        0 (0%)      0 (0%)           0 (0%)         8d
  kube-system                 kube-apiserver-minikube             250m (12%)    0 (0%)      0 (0%)           0 (0%)         8d
  kube-system                 kube-controller-manager-minikube    200m (10%)    0 (0%)      0 (0%)           0 (0%)         8d
  kube-system                 kube-proxy-hdvwk                    0 (0%)        0 (0%)      0 (0%)           0 (0%)         8d
  kube-system                 kube-scheduler-minikube             100m (5%)     0 (0%)      0 (0%)           0 (0%)         8d
  kube-system                 storage-provisioner                 0 (0%)        0 (0%)      0 (0%)           0 (0%)         8d
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests    Limits
  --------           --------    ------
  cpu                750m (37%)  0 (0%)
  memory             140Mi (3%)  340Mi (8%)
  ephemeral-storage  0 (0%)      0 (0%)
  hugepages-2Mi      0 (0%)      0 (0%)
Events:
  Type    Reason                   Age                    From                  Message
  ----    ------                   ----                   ----                  -------
  Normal  NodeNotReady             4d13h (x2 over 5d18h)  kubelet, minikube     Node minikube status is now: NodeNotReady
  Normal  NodeHasSufficientMemory  4d11h (x10 over 8d)    kubelet, minikube     Node minikube status is now: NodeHasSufficientMemory
  Normal  NodeHasNoDiskPressure    4d11h (x10 over 8d)    kubelet, minikube     Node minikube status is now: NodeHasNoDiskPressure
  Normal  NodeHasSufficientPID     4d11h (x10 over 8d)    kubelet, minikube     Node minikube status is now: NodeHasSufficientPID
  Normal  NodeReady                4d11h (x10 over 8d)    kubelet, minikube     Node minikube status is now: NodeReady
  Normal  Starting                 51m                    kubelet, minikube     Starting kubelet.
  Normal  NodeHasSufficientMemory  51m (x8 over 51m)      kubelet, minikube     Node minikube status is now: NodeHasSufficientMemory
  Normal  NodeHasNoDiskPressure    51m (x8 over 51m)      kubelet, minikube     Node minikube status is now: NodeHasNoDiskPressure
  Normal  NodeHasSufficientPID     51m (x7 over 51m)      kubelet, minikube     Node minikube status is now: NodeHasSufficientPID
  Normal  NodeAllocatableEnforced  51m                    kubelet, minikube     Updated Node Allocatable limit across pods
  Normal  Starting                 50m                    kube-proxy, minikube  Starting kube-proxy.
```

## Get Description of a single node 
```
$ kubectl describe nodes minikube
or
$ kubectl describe no minikube
```
##### Result
```
Name:               minikube
Roles:              master
Labels:             beta.kubernetes.io/arch=amd64
                    beta.kubernetes.io/os=linux
                    kubernetes.io/arch=amd64
                    kubernetes.io/hostname=minikube
                    kubernetes.io/os=linux
                    minikube.k8s.io/commit=57e2f55f47effe9ce396cea42a1e0eb4f611ebbd
                    minikube.k8s.io/name=minikube
                    minikube.k8s.io/updated_at=2020_06_11T19_02_35_0700
                    minikube.k8s.io/version=v1.11.0
                    node-role.kubernetes.io/master=
Annotations:        kubeadm.alpha.kubernetes.io/cri-socket: /var/run/dockershim.sock
                    node.alpha.kubernetes.io/ttl: 0
                    volumes.kubernetes.io/controller-managed-attach-detach: true
CreationTimestamp:  Thu, 11 Jun 2020 19:02:32 +0500
Taints:             <none>
Unschedulable:      false
Lease:
  HolderIdentity:  minikube
  AcquireTime:     <unset>
  RenewTime:       Sat, 20 Jun 2020 19:06:59 +0500
Conditions:
  Type             Status  LastHeartbeatTime                 LastTransitionTime                Reason                       Message
  ----             ------  -----------------                 ------------------                ------                       -------
  MemoryPressure   False   Sat, 20 Jun 2020 19:04:41 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasSufficientMemory   kubelet has sufficient memory available
  DiskPressure     False   Sat, 20 Jun 2020 19:04:41 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasNoDiskPressure     kubelet has no disk pressure
  PIDPressure      False   Sat, 20 Jun 2020 19:04:41 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletHasSufficientPID      kubelet has sufficient PID available
  Ready            True    Sat, 20 Jun 2020 19:04:41 +0500   Tue, 16 Jun 2020 06:59:23 +0500   KubeletReady                 kubelet is posting ready status
Addresses:
  InternalIP:  192.168.64.3
  Hostname:    minikube
Capacity:
  cpu:                2
  ephemeral-storage:  16954224Ki
  hugepages-2Mi:      0
  memory:             3936940Ki
  pods:               110
Allocatable:
  cpu:                2
  ephemeral-storage:  16954224Ki
  hugepages-2Mi:      0
  memory:             3936940Ki
  pods:               110
System Info:
  Machine ID:                 1407419cbe9e450887ca56f2c66dd91b
  System UUID:                13a811ea-0000-0000-b7da-acbc32793da9
  Boot ID:                    4dbb55d1-58af-44aa-ac1b-8d68ef5e9d9e
  Kernel Version:             4.19.107
  OS Image:                   Buildroot 2019.02.10
  Operating System:           linux
  Architecture:               amd64
  Container Runtime Version:  docker://19.3.8
  Kubelet Version:            v1.18.3
  Kube-Proxy Version:         v1.18.3
Non-terminated Pods:          (8 in total)
  Namespace                   Name                                CPU Requests  CPU Limits  Memory Requests  Memory Limits  AGE
  ---------                   ----                                ------------  ----------  ---------------  -------------  ---
  kube-system                 coredns-66bff467f8-hvbrm            100m (5%)     0 (0%)      70Mi (1%)        170Mi (4%)     9d
  kube-system                 coredns-66bff467f8-j6x25            100m (5%)     0 (0%)      70Mi (1%)        170Mi (4%)     9d
  kube-system                 etcd-minikube                       0 (0%)        0 (0%)      0 (0%)           0 (0%)         9d
  kube-system                 kube-apiserver-minikube             250m (12%)    0 (0%)      0 (0%)           0 (0%)         9d
  kube-system                 kube-controller-manager-minikube    200m (10%)    0 (0%)      0 (0%)           0 (0%)         9d
  kube-system                 kube-proxy-hdvwk                    0 (0%)        0 (0%)      0 (0%)           0 (0%)         9d
  kube-system                 kube-scheduler-minikube             100m (5%)     0 (0%)      0 (0%)           0 (0%)         9d
  kube-system                 storage-provisioner                 0 (0%)        0 (0%)      0 (0%)           0 (0%)         9d
Allocated resources:
  (Total limits may be over 100 percent, i.e., overcommitted.)
  Resource           Requests    Limits
  --------           --------    ------
  cpu                750m (37%)  0 (0%)
  memory             140Mi (3%)  340Mi (8%)
  ephemeral-storage  0 (0%)      0 (0%)
  hugepages-2Mi      0 (0%)      0 (0%)
Events:              <none>
```

## Create a pod through yaml file
create the below yaml file as mypod.yaml
```
kind: Pod
apiVersion: v1
metadata:
  name: myfirstpod
spec: 
  containers:
  - name: container1
    image: aamirpinger/helloworld:latest
    ports:
    - containerPort: 80
```

Run $ kubectl create -f <FILE_NAME>.yaml to create a pod

```
$ kubectl create -f mypod.yaml
```
##### Result
```
pod/myfirstpod created
```

## Get all pods
```
$ kubectl get pod
or
$ kubectl get pods
or
$ kubectl get po
```
##### Result
```
NAME         READY   STATUS    RESTARTS   AGE
myfirstpod   1/1     Running   0          5m48s
pod1         0/1     Error     0          9d
```

## Get info of a already created pod in yaml format
```
$ kubectl get po myfirstpod -o yaml
```
##### Result
```
apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: "2020-06-20T14:29:33Z"
  managedFields:
  - apiVersion: v1
    fieldsType: FieldsV1
    fieldsV1:
      f:spec:
        f:containers:
          k:{"name":"container1"}:
            .: {}
            f:image: {}
            f:imagePullPolicy: {}
            f:name: {}
            f:ports:
              .: {}
              k:{"containerPort":80,"protocol":"TCP"}:
                .: {}
                f:containerPort: {}
                f:protocol: {}
            f:resources: {}
            f:terminationMessagePath: {}
            f:terminationMessagePolicy: {}
        f:dnsPolicy: {}
        f:enableServiceLinks: {}
        f:restartPolicy: {}
        f:schedulerName: {}
        f:securityContext: {}
        f:terminationGracePeriodSeconds: {}
    manager: kubectl
    operation: Update
    time: "2020-06-20T14:29:33Z"
  - apiVersion: v1
    fieldsType: FieldsV1
    fieldsV1:
      f:status:
        f:conditions:
          k:{"type":"ContainersReady"}:
            .: {}
            f:lastProbeTime: {}
            f:lastTransitionTime: {}
            f:status: {}
            f:type: {}
          k:{"type":"Initialized"}:
            .: {}
            f:lastProbeTime: {}
            f:lastTransitionTime: {}
            f:status: {}
            f:type: {}
          k:{"type":"Ready"}:
            .: {}
            f:lastProbeTime: {}
            f:lastTransitionTime: {}
            f:status: {}
            f:type: {}
        f:containerStatuses: {}
        f:hostIP: {}
        f:phase: {}
        f:podIP: {}
        f:podIPs:
          .: {}
          k:{"ip":"172.17.0.4"}:
            .: {}
            f:ip: {}
        f:startTime: {}
    manager: kubelet
    operation: Update
    time: "2020-06-20T14:30:44Z"
  name: myfirstpod
  namespace: default
  resourceVersion: "376262"
  selfLink: /api/v1/namespaces/default/pods/myfirstpod
  uid: 5ab7d15c-ced3-43b5-baaf-3b9aa80f67f4
spec:
  containers:
  - image: aamirpinger/helloworld:latest
    imagePullPolicy: Always
    name: container1
    ports:
    - containerPort: 80
      protocol: TCP
    resources: {}
    terminationMessagePath: /dev/termination-log
    terminationMessagePolicy: File
    volumeMounts:
    - mountPath: /var/run/secrets/kubernetes.io/serviceaccount
      name: default-token-m7jwp
      readOnly: true
  dnsPolicy: ClusterFirst
  enableServiceLinks: true
  nodeName: minikube
  priority: 0
  restartPolicy: Always
  schedulerName: default-scheduler
  securityContext: {}
  serviceAccount: default
  serviceAccountName: default
  terminationGracePeriodSeconds: 30
  tolerations:
  - effect: NoExecute
    key: node.kubernetes.io/not-ready
    operator: Exists
    tolerationSeconds: 300
  - effect: NoExecute
    key: node.kubernetes.io/unreachable
    operator: Exists
    tolerationSeconds: 300
  volumes:
  - name: default-token-m7jwp
    secret:
      defaultMode: 420
      secretName: default-token-m7jwp
status:
  conditions:
  - lastProbeTime: null
    lastTransitionTime: "2020-06-20T14:29:33Z"
    status: "True"
    type: Initialized
  - lastProbeTime: null
    lastTransitionTime: "2020-06-20T14:30:44Z"
    status: "True"
    type: Ready
  - lastProbeTime: null
    lastTransitionTime: "2020-06-20T14:30:44Z"
    status: "True"
    type: ContainersReady
  - lastProbeTime: null
    lastTransitionTime: "2020-06-20T14:29:33Z"
    status: "True"
    type: PodScheduled
  containerStatuses:
  - containerID: docker://4bc0871891d1907ec1e314a0aa99842c8ed41344609df8bdc49fc78db83652d6
    image: aamirpinger/helloworld:latest
    imageID: docker-pullable://aamirpinger/helloworld@sha256:32dea8e4d394edc996c62648e0abc90ec3371ada9e30decfc733ae7160e21466
    lastState: {}
    name: container1
    ready: true
    restartCount: 0
    started: true
    state:
      running:
        startedAt: "2020-06-20T14:30:44Z"
  hostIP: 192.168.64.3
  phase: Running
  podIP: 172.17.0.4
  podIPs:
  - ip: 172.17.0.4
  qosClass: BestEffort
  startTime: "2020-06-20T14:29:33Z"
```
## Get info of a already created pod in json format
```
$ kubectl get po <POD_NAME> -o json
```
as
```
$ kubectl get po myfirstpod -o json
```
##### Result
```
{
    "apiVersion": "v1",
    "kind": "Pod",
    "metadata": {
        "creationTimestamp": "2020-06-20T14:29:33Z",
        "managedFields": [
            {
                "apiVersion": "v1",
                "fieldsType": "FieldsV1",
                "fieldsV1": {
                    "f:spec": {
                        "f:containers": {
                            "k:{\"name\":\"container1\"}": {
                                ".": {},
                                "f:image": {},
                                "f:imagePullPolicy": {},
                                "f:name": {},
                                "f:ports": {
                                    ".": {},
                                    "k:{\"containerPort\":80,\"protocol\":\"TCP\"}": {
                                        ".": {},
                                        "f:containerPort": {},
                                        "f:protocol": {}
                                    }
                                },
                                "f:resources": {},
                                "f:terminationMessagePath": {},
                                "f:terminationMessagePolicy": {}
                            }
                        },
                        "f:dnsPolicy": {},
                        "f:enableServiceLinks": {},
                        "f:restartPolicy": {},
                        "f:schedulerName": {},
                        "f:securityContext": {},
                        "f:terminationGracePeriodSeconds": {}
                    }
                },
                "manager": "kubectl",
                "operation": "Update",
                "time": "2020-06-20T14:29:33Z"
            },
            {
                "apiVersion": "v1",
                "fieldsType": "FieldsV1",
                "fieldsV1": {
                    "f:status": {
                        "f:conditions": {
                            "k:{\"type\":\"ContainersReady\"}": {
                                ".": {},
                                "f:lastProbeTime": {},
                                "f:lastTransitionTime": {},
                                "f:status": {},
                                "f:type": {}
                            },
                            "k:{\"type\":\"Initialized\"}": {
                                ".": {},
                                "f:lastProbeTime": {},
                                "f:lastTransitionTime": {},
                                "f:status": {},
                                "f:type": {}
                            },
                            "k:{\"type\":\"Ready\"}": {
                                ".": {},
                                "f:lastProbeTime": {},
                                "f:lastTransitionTime": {},
                                "f:status": {},
                                "f:type": {}
                            }
                        },
                        "f:containerStatuses": {},
                        "f:hostIP": {},
                        "f:phase": {},
                        "f:podIP": {},
                        "f:podIPs": {
                            ".": {},
                            "k:{\"ip\":\"172.17.0.4\"}": {
                                ".": {},
                                "f:ip": {}
                            }
                        },
                        "f:startTime": {}
                    }
                },
                "manager": "kubelet",
                "operation": "Update",
                "time": "2020-06-20T14:30:44Z"
            }
        ],
        "name": "myfirstpod",
        "namespace": "default",
        "resourceVersion": "376262",
        "selfLink": "/api/v1/namespaces/default/pods/myfirstpod",
        "uid": "5ab7d15c-ced3-43b5-baaf-3b9aa80f67f4"
    },
    "spec": {
        "containers": [
            {
                "image": "aamirpinger/helloworld:latest",
                "imagePullPolicy": "Always",
                "name": "container1",
                "ports": [
                    {
                        "containerPort": 80,
                        "protocol": "TCP"
                    }
                ],
                "resources": {},
                "terminationMessagePath": "/dev/termination-log",
                "terminationMessagePolicy": "File",
                "volumeMounts": [
                    {
                        "mountPath": "/var/run/secrets/kubernetes.io/serviceaccount",
                        "name": "default-token-m7jwp",
                        "readOnly": true
                    }
                ]
            }
        ],
        "dnsPolicy": "ClusterFirst",
        "enableServiceLinks": true,
        "nodeName": "minikube",
        "priority": 0,
        "restartPolicy": "Always",
        "schedulerName": "default-scheduler",
        "securityContext": {},
        "serviceAccount": "default",
        "serviceAccountName": "default",
        "terminationGracePeriodSeconds": 30,
        "tolerations": [
            {
                "effect": "NoExecute",
                "key": "node.kubernetes.io/not-ready",
                "operator": "Exists",
                "tolerationSeconds": 300
            },
            {
                "effect": "NoExecute",
                "key": "node.kubernetes.io/unreachable",
                "operator": "Exists",
                "tolerationSeconds": 300
            }
        ],
        "volumes": [
            {
                "name": "default-token-m7jwp",
                "secret": {
                    "defaultMode": 420,
                    "secretName": "default-token-m7jwp"
                }
            }
        ]
    },
    "status": {
        "conditions": [
            {
                "lastProbeTime": null,
                "lastTransitionTime": "2020-06-20T14:29:33Z",
                "status": "True",
                "type": "Initialized"
            },
            {
                "lastProbeTime": null,
                "lastTransitionTime": "2020-06-20T14:30:44Z",
                "status": "True",
                "type": "Ready"
            },
            {
                "lastProbeTime": null,
                "lastTransitionTime": "2020-06-20T14:30:44Z",
                "status": "True",
                "type": "ContainersReady"
            },
            {
                "lastProbeTime": null,
                "lastTransitionTime": "2020-06-20T14:29:33Z",
                "status": "True",
                "type": "PodScheduled"
            }
        ],
        "containerStatuses": [
            {
                "containerID": "docker://4bc0871891d1907ec1e314a0aa99842c8ed41344609df8bdc49fc78db83652d6",
                "image": "aamirpinger/helloworld:latest",
                "imageID": "docker-pullable://aamirpinger/helloworld@sha256:32dea8e4d394edc996c62648e0abc90ec3371ada9e30decfc733ae7160e21466",
                "lastState": {},
                "name": "container1",
                "ready": true,
                "restartCount": 0,
                "started": true,
                "state": {
                    "running": {
                        "startedAt": "2020-06-20T14:30:44Z"
                    }
                }
            }
        ],
        "hostIP": "192.168.64.3",
        "phase": "Running",
        "podIP": "172.17.0.4",
        "podIPs": [
            {
                "ip": "172.17.0.4"
            }
        ],
        "qosClass": "BestEffort",
        "startTime": "2020-06-20T14:29:33Z"
    }
}
```
