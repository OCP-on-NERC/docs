# OpenShift Software Components

## Installation tooling

- OpenShift Assisted Installer

## OpenShift version

- OpenShift 4.10 (if it's released by the time we start installing things)

## Identity Management

- TBD: IDM/SSO
- [ColdFront][]

[coldfront]: https://coldfront.readthedocs.io/en/latest/

## Networking

- [OVNKubernetes][] (this is the default [SDN][] driver with recent versions of OpenShift)
- [Nmstate][]
- [MetalLB][]

[ovnkubernetes]: https://github.com/ovn-org/ovn-kubernetes
[nmstate]: https://nmstate.io/
[metallb]: https://metallb.universe.tf/
[sdn]: https://en.wikipedia.org/wiki/Software-defined_networking

## Monitoring/alerting/logging

- [Prometheus][]
- [Grafana][]
- [Loki][]

[prometheus]: https://prometheus.io/
[grafana]: https://grafana.com/
[loki]: https://grafana.com/oss/loki/

## Certificate provisioning

- [Cert-manager][]
- TBD: DNS API for LetsEncrypt DNS-01 challenges

[cert-manager]: https://cert-manager.io/docs/

## Secrets management

- Hashicorp [Vault][]
- [External Secrets][]

[external secrets]: https://github.com/external-secrets/kubernetes-external-secrets
[vault]: https://www.vaultproject.io/

## Storage

- [OpenShift Data Foundation][odf] (ODF, née OCS)
- [Snapscheduler][]
- [Volsync][]

[odf]: https://www.redhat.com/en/technologies/cloud-computing/openshift-data-foundation
[snapscheduler]: https://github.com/backube/snapscheduler
[volsync]: https://github.com/backube/volsync
