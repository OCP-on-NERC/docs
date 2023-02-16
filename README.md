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

## Validations make your life easier

### Pre-commit checks

Configure linters to run before each commit by installing the
`pre-commit` tool:

```
pip install pre-commit
```

And then enabling it for your working directory. From inside this
repository, run:

```
pre-commit install
```

## Observability Monitoring and Cluster Logging

- To learn more about the project's [Advanced Cluster Management Observability Monitoring click here](monitoring-and-logging.md#monitoring)
- To learn more about the project's [OpenShift Cluster Logging with Loki click here](monitoring-and-logging.md#logging)
