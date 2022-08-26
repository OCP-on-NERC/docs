# Monitoring

- Monitoring in the cluster is provided by the Red Hat [Advanced Cluster Management Operator here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/open-cluster-management/operators.coreos.com~v1alpha1~ClusterServiceVersion/advanced-cluster-management.v2.5.1).

## MultiClusterObservability component
- The ACM MultiClusterObservability component allows us to configure the storage class, storage size, rule storage size, receive storage size, compact storage size, alert manager storage size, metric object storage bucket, interval, and downsampling of the observability. It also allows us to configure the replicas and node selectors for each of the observability components (store, receive, grafana, query, alert manager, store memcached, RBAC query proxy, observatorium API, query frontend, rule, and query frontend memcached. See the [Multi Cluster Observability component here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/cluster/observability.open-cluster-management.io~v1beta2~MultiClusterObservability/observability).
- You can find the observability components in the [open-cluster-management-observability namespace here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/search/ns/open-cluster-management-observability?kind=apps%7Ev1%7EDeployment%2Capps%7Ev1%7EStatefulSet%2Croute.openshift.io%7Ev1%7ERoute%2Ccore%7Ev1%7EService).

# MultiClusterObservability documentation

Here are some useful links to the MultiClusterObservability documentation:

- [APIs Red Hat Advanced Cluster Management for Kubernetes 2.5](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.5/html/apis/apis#rhacm-docs_apis_multiclusterobservability_jsonmulticlusterobservability_observabilityadvanced)
- [Observing environments introduction Red Hat Advanced Cluster Management for Kubernetes 2.5](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.5/html/observability/observing-environments-intro#enabling-observability)
- [Managing applications Red Hat Advanced Cluster Management for Kubernetes 2.0](https://access.redhat.com/documentation/en-us/red_hat_advanced_cluster_management_for_kubernetes/2.0/html/manage_applications/managing-applications)
