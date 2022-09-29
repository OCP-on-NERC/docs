# Monitoring

- Monitoring in the cluster is provided by the Red Hat [Advanced Cluster Management Operator here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/open-cluster-management/operators.coreos.com~v1alpha1~ClusterServiceVersion/advanced-cluster-management.v2.5.1).

## MultiClusterObservability component
- The ACM MultiClusterObservability component allows us to configure the storage class, storage size, rule storage size, receive storage size, compact storage size, alert manager storage size, metric object storage bucket, interval, and downsampling of the observability. It also allows us to configure the replicas and node selectors for each of the observability components (store, receive, grafana, query, alert manager, store memcached, RBAC query proxy, observatorium API, query frontend, rule, and query frontend memcached. See the [Multi Cluster Observability component here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/cluster/observability.open-cluster-management.io~v1beta2~MultiClusterObservability/observability).
- You can find the observability components in the [open-cluster-management-observability namespace here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/search/ns/open-cluster-management-observability?kind=apps%7Ev1%7EDeployment%2Capps%7Ev1%7EStatefulSet%2Croute.openshift.io%7Ev1%7ERoute%2Ccore%7Ev1%7EService).

# Using the Monitoring tools

## Monitoring and logging for the infrastructure hardware and software that is not OpenShift (for example Grafana).

As a NERC administrator, I should be able to monitor the status of any infrastructure software or hardware that supports operations for the NERC OpenShift environment, even if it is not itself part of OpenShift.

## Steps for reporting

You can access many metrics for pods of a particular application like grafana or loki.

- [Click here to visit the cpu usage logs for grafana](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum_rate%7Bnamespace%3D%5C%22grafana%5C%22%7D%22%7D%5D).
- [Click here to visit the cpu usage logs for loki](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum_rate%7Bnamespace%3D%5C%22openshift-operators-redhat%5C%22%7D%22%7D%5D).

# Using the Reporting tools

## Track/report usage of the cluster

As an administrator of the cluster, I should be able to view daily, weekly and monthly reports of the cluster infrastructure utilization.

### Steps

- Administrator logs into the associated XDMoD instance and views reports.
- [Click here to view the ACM Observability Grafana dashboards](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/). These dashboards provide insights into Control Plane Health, Optimization, Capacity, Utilization and more. You can change the timespan in the top right to show results in terms of minutes, hours, days, months or years.

## Track/report usage of the project
As a user and the owner of a project, I should be able to view daily, weekly and monthly reports of the infrastructure utilization by the projects I own.

### Steps to track usage

- User logs into the associated XDMoD instance and views reports for projects they own.
- User cannot view reports for projects they do not own. We will need to look into this, to restrict the view to only projects that they own.
- [Click here to view the memory usage of projects over time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22namespace:container_memory_usage_bytes:sum%22%7D%5D).
- [Click here to view the cpu usage of the projects over time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum%22%7D%5D).
- [Click here to show the projects using the top 5 cpu usage at each point in time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22topk%285,%20%281%20-%20avg%28rate%28node_namespace_pod_container:container_cpu_usage_seconds_total:sum%7B%7D%5B$__rate_interval%5D%29%29%20by%20%28namespace%29%29%29%22%7D%5D).

# MultiClusterObservability documentation

Here are some useful links to the MultiClusterObservability documentation:

- [APIs Red Hat Advanced Cluster Management for Kubernetes 2.5](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.5/html/apis/apis#rhacm-docs_apis_multiclusterobservability_jsonmulticlusterobservability_observabilityadvanced)
- [Observing environments introduction Red Hat Advanced Cluster Management for Kubernetes 2.5](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.5/html/observability/observing-environments-intro#enabling-observability)
- [Managing applications Red Hat Advanced Cluster Management for Kubernetes 2.0](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.0/html/manage_applications/managing-applications)
