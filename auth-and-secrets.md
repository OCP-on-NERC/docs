# Authentication, Authorization, and Secrets

## Authentication configuration on nerc-ocp-infra

The `nerc-ocp-infra` cluster is configured to authenticate against the [ocp-on-nerc organization][] on GitHub (see the [`Oauth` resource][oauth]). Only members of the `nerc-ops` team will be able to authenticate.

[ocp-on-nerc organization]: https://github.com/OCP-on-NERC
[oauth]: https://github.com/OCP-on-NERC/nerc-ocp-config/blob/main/cluster-scope/overlays/nerc-ocp-infra/oauths/cluster_patch.yaml

## Authorization configuration

We are running an instance of the [group-sync-operator][] to synchronize GitHub teams with OpenShift groups. We see the following groups in our OpenShift deployment:

[group-sync-operator]: https://github.com/redhat-cop/group-sync-operator

- `cluster-admins`
- `nerc-docs`
- `nerc-ops`
- `nerc-org-admins`

We grant members of the `nerc-ops` both the [`cluster-reader` role][cluster-reader] and the [`sudoers` role][sudoers]. The `cluster-reader` role grants *read-only* access to *most* cluster resources (it specifically excludes secrets, and it may exclude a smattering of custom resource types).

The `sudoers` role grants the ability to [impersonate][] other users, in particular the `system:admin` user. You will need to do this in order to create or modify resources, or to view resources that aren't visible to the `cluster-reader` role.  For example, to get a list of secrets in the `openshift-config` namespace:

```
kubectl --as system:admin -n openshift-config get secret
```

It is also possible to impersonate the `system:admin` user through the console UI:

1. Select "User Management" from the left navigation menu
1. Select "RoleBindings" from the "User Management" sub menu
1. Use the filter to search for `cluster-admins`
1. Click on the "⋮" menu next to the `cluster-admins` rolebinding for the `system:admin` user and select 'Impersonate user "system:admin"'.

[cluster-reader]: https://github.com/OCP-on-NERC/nerc-ocp-config/blob/main/cluster-scope/overlays/nerc-ocp-infra/clusterrolebindings/nerc-ops-cluster-reader.yaml
[sudoers]: https://github.com/OCP-on-NERC/nerc-ocp-config/blob/main/cluster-scope/overlays/nerc-ocp-infra/clusterrolebindings/nerc-ops-sudoers.yaml
[impersonate]: https://docs.openshift.com/container-platform/4.10/authentication/impersonating-system-admin.html

## Secrets management

Secrets in the cluster are managed through the use of [Hashicorp Vault][] and the [External Secrets operator][]. The `nerc-ocp-infra` cluster has a single `ClusterSecretStore`; other clusters will probably have per-namespace `SecretStore` resources in order to avoid accidentally exposing secrets. Our [vault instance][] is hosted at <https://vault-ui-vault.apps.nerc-ocp-infra.rc.fas.harvard.edu>.

[hashicorp vault]: https://www.vaultproject.io/
[external secrets operator]: https://external-secrets.io/
[vault instance]: https://vault-ui-vault.apps.nerc-ocp-infra.rc.fas.harvard.edu/

To add a secret to OpenShift:

1. Create the secret in our [vault instance][]. Generally, the path for a secret will be something like `nerc/<cluster>/<namespace>/<name>`. For example, the default ingress certificate and key are stored at `nerc/nerc-ocp-infra/openshift-ingress/default-ingress-certificate`.
1. Create an appropriate `ExternalSecret` resource to pull the secret into OpenShift and add it to the config repository.

There are some example `ExternalSecrets` in the config repository.

### Vault authentication

We are running an instance of [Dex][] on the `nerc-ocp-infra` cluster to act as an authentication bridge between Vault and OpenShift. Using Dex, Vault can authenticate against OpenShift and can make use of OpenShift groups for authorization purposes.

Members of the `nerc-ops` group will be able to list, view, modify, and create secrets in the `nerc/` secrets engine.

Members of the `nerc-org-admins` group have the ability to manage most Vault configurations.

[Dex]: https://github.com/dexidp/dex


## Managing vault configuration

Our Vault deployment cannot be configured using Kubernetes resources. In order to provide a change history and mechanism for reconstituting the configuration if we have to start from scratch, we are managing the vault configuration through a set of Ansible playbooks hosted at <https://github.com/OCP-on-NERC/vault-config>.
