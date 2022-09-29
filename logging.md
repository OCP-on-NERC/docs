# Cluster Logging

- Logging in the cluster is provided by the Red Hat [Red Hat OpenShift Logging here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-logging/operators.coreos.com~v1alpha1~ClusterServiceVersion/cluster-logging.5.5.0).
- We combine the OpenShift Logging Operator with the [Loki Operator here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-operators-redhat/operators.coreos.com~v1alpha1~Subscription/loki-operator), so that the Logging Operator sends the infrastructure, audit, and application logs to the Loki Operator where they are stored in an Object Bucket.
- The OpenShift Logging Operator has a dependency on the [Elasticsearch Operator here](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-operators-redhat/operators.coreos.com~v1alpha1~Subscription/elasticsearch-operator). Whether you use Elasticsearch for storing logs or using Loki, you still need the Elasticsearch Operator installed for required dependent CustomResourceDefinitions.

## Loki operator

- The Loki Operator allows you to setup LokiStacks, AlertingRules, RecordingRules, and RulerConfigs based on your cluster logs for infrastructure, audit, and applications. See the [ Loki Operator here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-operators-redhat/operators.coreos.com~v1alpha1~ClusterServiceVersion/loki-operator.5.4.6)
- Setting up a LokiStack allows you to configure the size of a cluster logging system that you desire in terms of storage and replicas. [ LokiStack here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-operators-redhat/loki.grafana.com~v1beta1~LokiStack/lokistack)
- Setting up a LokiStack involves configuring persistent storage by storageClassName for Persistent Volume Claims. [ ocs-external-storagecluster-ceph-rbd storage class here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/cluster/storageclasses/ocs-external-storagecluster-ceph-rbd)
- Setting up a LokiStack involves configuring an object storage by a secret named "thanos-object-storage" in the "openshift-operators-redhat" namespace containing the access_key_id, access_key_secret, bucketnames, and endpoint of the object storage.
- The object storage for Loki is provided by OpenShift Data Foundations. See the [ openshift-operators-redhat-objectbucketclaim Object Bucket Claim here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/openshift-operators-redhat/objectbucket.io~v1alpha1~ObjectBucketClaim/openshift-operators-redhat-objectbucketclaim)

## Grafana operator

- The Grafana Operator allows you to setup Grafana instances, datasources, dashboards, and notification channels. See the [ Grafana Operator here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/grafana/operators.coreos.com~v1alpha1~ClusterServiceVersion/grafana-operator.v4.6.0)
- We configure a logging-grafana Grafana instance. See the [ Logging Grafana instance here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/grafana/clusterserviceversions/grafana-operator.v4.6.0/integreatly.org~v1alpha1~Grafana/logging-grafana)
- We configure a loki-datasource for Grafana to access the Loki Cluster Logs. See the [ Loki Datasource here ](https://console-openshift-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/k8s/ns/grafana/clusterserviceversions/grafana-operator.v4.6.0/integreatly.org~v1alpha1~GrafanaDataSource/loki-datasource)
- The [ Grafana Dashboard for Cluster Logs is available here ](https://logging-grafana.apps.nerc-ocp-infra.rc.fas.harvard.edu)


# Tracking events in the Logging System

As an administrator of the cluster, I should be able to track all the events in the cluster using the logging system in OpenShift.

## Steps

- [Click here to visit the Logging Grafana instance](https://logging-grafana.apps.nerc-ocp-infra.rc.fas.harvard.edu).
- Click on the "Explore" button which looks like a compass on the left side. At the top of that page, you can select from the dropdown the infrastructure, audit or application logs. You can then use the Log Browser to browse the different labels like kubernetes_host and select a value for a tag to filter in on actual search results. Continue to add more labels and values to narrow in on the logs you wish to see.
- You can build custom dashboards and alerts in this Logging Grafana instance.

# Cluster Logging documentation

Here are some useful links to the MultiClusterObservability documentation:

- [Chapter 7. Forwarding logs to external third-party logging systems OpenShift Container Platform 4.10](https://access.redhat.com/documentation/en-us/openshift_container_platform/4.10/html/logging/cluster-logging-external#cluster-logging-collector-log-forward-loki_cluster-logging-external)
- [Logging OpenShift Container Platform 4.10](https://access.redhat.com/documentation/en-us/openshift_container_platform/4.10/html-single/logging/index#cluster-logging-exported-fields-kubernetes_cluster-logging-exported-fields)
- [Exported fields | Logging | OpenShift Container Platform 4.10](https://docs.openshift.com/container-platform/4.10/logging/cluster-logging-exported-fields.html#cluster-logging-exported-fields-kubernetes_cluster-logging-exported-fields)
- [Deploying Cluster Logging](https://docs.openshift.com/container-platform/4.10/logging/cluster-logging-deploying.html)
- [Multi-tenancy | Grafana Loki documentation](https://grafana.com/docs/loki/latest/operations/multi-tenancy/)
- [Grafana Configuration](https://grafana.com/docs/loki/latest/configuration/)
- [HTTP API | Grafana Loki documentation](https://grafana.com/docs/loki/latest/api/#push-log-entries-to-loki)
- [Forwarding Logs to LokiStack - Loki Operator](https://loki-operator.dev/docs/forwarding_logs_to_gateway.md/)
- [API - Loki Operator](https://loki-operator.dev/docs/api.md/#opaspec)
- [Configure generic OAuth authentication | Grafana documentation](https://grafana.com/docs/grafana/latest/setup-grafana/configure-security/configure-authentication/generic-oauth/)
