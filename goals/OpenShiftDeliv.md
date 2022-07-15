
## OpenShift Cluster Deliverable Checklist

Minimum list of required items to complete initial OpenShift install phase of OCP-on-NERC project.  All documents on checklist are drafts and do not require NERC review at this stage.

- [ ] Secrets required for installing and operating OCP created and stored (not in public repo).

- [ ] Additional software required for installing/supporting basic production OCP (e.g. Vault) installed and running.

- [ ] Admin accounts and access to OCP and additional required software/infrastucture for NERC, MOC and Red Hat admin staff created and tested.

- [ ] All NERC staff added to OCP-on-NERC github repositories.

- [ ] Storage adequate to hold one month of OCP and associated required software logs configured and tested.  (Archiving not required at this stage.)

- [ ] OCP interfaces required to proceed with integration for ColdFront and XDMod are installed and working as expected.

- [ ] OCP dashboards needed for routine opertions and debugging are configured and available to admin users only.

- [ ] Prometheus operator configured and collecting metrics for production infrastructure.

- [ ] Resources, storage and interfaces needed to configure and install Grafana for monitoring and alerting on OCP are available and ready for Grafana integration.

- [ ] Specific operations procedures for bringing up OCP and related required software in NERC automated to the extent possible and documented where automation is not possible.

- [ ] Specific operations procedures for shutting down OCP and related required software in NERC automated to the extent possible and documented where automation is not possible.

- [ ] Demonstrate installation and successful operation of infra cluster. (Recorded screenshare with comments is sufficient.  Live demo not required.)

- [ ] Configure all worker nodes that are available in this phase of NERC deployment.

- [ ] Demonstrate adding/deleting worker nodes to the cluster, verifying that all available worker nodes are in "ready" state.

- [ ] Demonstrate creating/deleting multiple users and projects with OCP (no ColdFront), including demonstrating that the demo users can install software in their demo project containers.

- [ ] Document operations procedure for responding to a security event for NERC resources currently available at this stage of NERC operation.  (This assumes the event is reported from outside this OCP cluster, e.g. a security alert that affects OCP is announced at Red Hat. or a NERC staff person reports a network infrastructure breach in email.)
