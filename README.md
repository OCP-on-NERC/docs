Documentation for the OCP on NERC project.

## Repositories

- [docs][] (this repository): Documentation for the OCP on NERC project
- [workflows][]: common GitHub workflows shared by all the repositories in this organization
- [nerc-ansible][]: Ansible inventory and playbooks for managing the nodes that comprise our OpenShift clusters
- [nerc-ocp-apps][] contains ArgoCD `Applications` and `ApplicationSets` that are consumed by the ArgoCD instance on the `nerc-infra` cluster
- [nerc-ocp-config][] contains manifests used to configure NERC OpenShift clusters. These manifests are deployed by ArgoCD using the configurations from the [apps repo][nerc-ocp-apps].

[docs]: https://github.com/ocp-on-nerc/docs
[workflows]: https://github.com/ocp-on-nerc/workflows
[nerc-ansible]: https://github.com/ocp-on-nerc/nerc-ansible
[nerc-ocp-apps]: https://github.com/ocp-on-nerc/nerc-ocp-apps
[nerc-ocp-config]: https://github.com/ocp-on-nerc/nerc-ocp-config
