# Design considerations for the NERC cluster

## Scaling goals

The initial hardware deployment is going to have just under 100 nodes. We need to know the growth plans for this cluster (and a rough timeline) to appropriately plan the cluster architecture. What makes sense for 100 nodes doesn't necessarily make sense for 1000 nodes.

There is some information in "[Planning your environment according to object maximums][max]" concerning maximum tested scalability limits for OpenShift.

[max]: https://docs.openshift.com/container-platform/4.9/scalability_and_performance/planning-your-environment-according-to-object-maximums.html

## Public vs. private networks

The Operate First clusters are installed primarily on public networks. This isn't necessarily a desirable model; for the NERC cluster, we probably want in-cluster traffic isolated to a private network, with only specific services exposed on a public address (either via [ingress sharding][] or via a [load balancer][]).

[ingress sharding]: https://docs.openshift.com/container-platform/4.9/networking/configuring_ingress_cluster_traffic/configuring-ingress-cluster-traffic-ingress-controller.html
[load balancer]: https://docs.openshift.com/container-platform/4.9/networking/metallb/about-metallb.html

We will also want to isolate storage traffic on a separate interface.  Given that our initial hardware all has dual 10Gb network interfaces, we'll probaly want (a) all storage traffic on one interface, and then (b) both in-cluster and public networks as vlans on a second interface.

## Connectivity to storage

Will the NERC OpenShift nodes be connected directly (e.g. via layer 2) to a NESE service network, or will they have routed (layer 3) access to NESE storage? This has implications for the network configuration, particularly if we're using the [OVNKubernetes][] SDN driver.

[ovnkubernetes]: https://docs.openshift.com/container-platform/4.9/networking/ovn_kubernetes_network_provider/about-ovn-kubernetes.html

## Rack diversity

We will ideally be able to spread cluster nodes across multiple racks in order to provide resiliency in the face of failures at the rack level (e.g., faulty PDUs or top-of-rack switches). With appropriate node labelling we can take advantage of this to create availability zones and ensure that service replicas are running in different racks.
