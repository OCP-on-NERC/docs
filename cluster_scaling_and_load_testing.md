# Cluster Scaling and load testing

## Cluster Scaling

We will initially be starting out with 3 Control nodes and 5 worker nodes. From here will will scale up at intervals of 10 worker nodes per until we reach the maximum number of available nodes.

## Interval Testing

After each interval reports that the nodes are ready we will use [kube-burner][1]. The goal here is two-fold. First we want to make sure that we can schedule pods on each node, and second that we can max out node capacity without needing to add infra nodes to support the three controller nodes.

## Key Performance Indicators

- Kubelet and CRI-O CPU and Memory Usage
- API Server and ETCD CPU and Memory Usage
- Control Node and Worker Node CPU and Memory Usage
- API Response Latency (99th percentile)
- ETCD No leader elections
- Pod Latencies, Scheduling and Ready
- Cluster Operator Health

## Tests

These tests are based on [examples][2] provided by the [kube-burner][1] project.

**kubelet-density-heavy**:

Verifies maximum pods per node. It creates a client/server application consisting of a basic application which performs queries in a pod running PostgreSQL and uses a k8s service to communicate with it.

| Worker Nodes | Pods | Containers | Projects |
| --- | --- | ---| --- |
| 5 | 90 | 180 | 9 |
| 15 | 270 | 540 | 26 |
| 25 | 450 | 900 | 43 |
| 35 | 630 | 1260 | 60 |
| 45 | 810 | 1620 | 77 |
| 55 | 990 | 1980 | 94 |
| 65 | 1170 | 2340 | 111 |

*18 pods per node, 2 containers per pod*

*1.7 projects per node, rounded up*

**cluster-density**

This workload creates resources such as builds and routes to stress the OpenShift control plane.

| Worker Nodes | Projects | ConfigMaps | ClusterIP Services | Secrets | Deployments/ReplicaSets |
| --- | --- | --- | --- | --- | --- |
| 5 | 3 | 45 | 50 | 55 | 8 |
| 15 | 9 | 135 |150 |165 |23 |
| 25 | 15 | 225| 250 | 275 | 38 |
| 35 | 21 | 315| 350 | 385 | 53 |
| 45 | 27 | 405| 450 | 495 | 68 |
| 55 | 33 | 495| 550 | 605 | 83 |
| 65 | 39 | 585| 650 | 715 | 98 |

*0.6 Projects per worker node*

*9 configMaps per worker node*

*10 clusterIPServices per worker node*

*11 secrets per worker node*

*1.5 deploymenys and replicaSets per worker node*

[1]: https://kube-burner.readthedocs.io/en/latest/
[2]: https://github.com/cloud-bulldozer/kube-burner/tree/master/examples/workloads
