# Cluster Validation Checklist
## Check general cluster status

 - [ ] Review installation log
   Check for any glaring issues, this could be image pull back off errors, storage issues, network failers, or permissions issues. The cluster admin credentials can be pulled from here as well.
   Install logs can be found on the install node, inside of the install directory
   ```shell
   $ cat <install_dir>/.openshift_install.log
   ```

 - [ ] Verify that image pull source is what is expected
   Check that the source of your openshift images is as expected.
   As we are not in a disconnected environment quay.io and the internal cluster registry.
   ```shell
   $ oc adm node-logs <node_name> -u crio
   ```

 - [ ] Verify that cluster version matches what is expected
   Check the `<cluster-type>_cluser_info.yaml` file in this repo to verifying the intended version for this cluster.
   ```shell
   $ oc get clusterversion
   ```

 - [ ] Verify that the cluster is on the correct update channel
   Currently we're looking at the stable update channel for 4.10
   ```shell
   $ oc get clusterversion -o jsonpath='{.items[0].spec}{"\n"}'
   ```

 - [ ] Check for any available cluster updates
   In the event that a new release has been made available during install check we are on the latest version.
   ```shell
   $ oc adm upgrade
   ```
 
## Verify operator availability

 - [ ] Verify that expected Operators are available
   We need to generate an initial list of operators that each cluster requires.
   ```shell
   $ oc get clusteroperators
   ```

 - [ ] Check that all csrs required by operators are approved.
   Check all nodes are in ready status and CSRs are approved.
   ```shell
   $ oc get csr
   ```

 - [ ] Approve any pending CSRs
   Verify that all pending CSRs are legitimate. If they are not approve only the legitimate CSRs one at a time.
   ```shell
   $ oc adm certificate approve <csr_name>
   ```
   If all CSRs are legitimate you can approve all pending all CSRs with the below command.
   ```shell
   $ oc get csr -o go-template='{{range .items}}{{if not .status}}{{.metadata.name}}{{"\n"}}{{end}}{{end}}' | xargs oc adm certificate approve
   ```

## Verify node health

 - [ ] List nodes
   Ensure that all nodes are in a Ready state and all nodes you expect to be available are
   ```shell
   $ oc get nodes
   ```

 - [ ] Review CPU and memory resources
   Ensure that all hardware expected is listed and that the load is in a the expected range
   ```shell
   $ oc adm top nodes
   ```

 - [ ] Ensure kubelet is running on each node
   Start a debug container on the node
   ```shell
   $ oc debug node <node_name>
   ```
   Set /host as your root directory
   ```shell
   # chroot /host
   ```
   Check the status of kubelet
   ```shell
   # systemctl status kubelet
   ```
