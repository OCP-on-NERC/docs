These acceptance tests are based on the [NERC Operational Use Cases](https://docs.google.com/document/u/0/d/1dHHpWvJD4b1mdXTDQhgWhiGeOLY7N7FmwvgI5VB3tP0/edit).

Reference for NERC OpenStack: [https://nerc-project.github.io/nerc-docs/get-started/user-onboarding-on-NERC/](https://nerc-project.github.io/nerc-docs/get-started/user-onboarding-on-NERC/)


## Managing Users



1. **Request a new account**
    * _As a new user, I should be able to create an account for myself in the NERC._
    * <span style="text-decoration:underline;">Steps</span>
        1. A prospective user follows the steps documented in [https://nerc-project.github.io/nerc-docs/get-started/create-a-user-portal-account/](https://nerc-project.github.io/nerc-docs/get-started/create-a-user-portal-account/) to create an account on the NERC.
2. **Remove a user**
    * _As an administrator, I should be able to remove a user, labels association with the user, and user identity from the cluster._
       * _(This step is generally unnecessary, given that a user that doesn’t have authorization to any project, cannot access any allocations, therefore removing a user from allocations is generally enough.)_
    * <span style="text-decoration:underline;">Steps</span>
        1. A NERC admin uses a private runbook to disable/ deactivate a user from KeyCloak.
        2. _(Optional)_ After that is done, the NERC admin uses the OpenShift CLI and runs the following:
            1. `oc delete user &lt;username>`
            2. `oc delete identity &lt;identity_provider>:&lt;username>`
        3. The user can no longer access OpenShift with their credentials
3. **Add/Remove PI privilege to a user**
    * _For any user account, the administrator should be able to add or remove PI status associated with that account.  A user may be a PI on multiple projects, but a project can have only 1 PI._
    * <span style="text-decoration:underline;">Steps</span>
        1. User creates a new account as described in section 1.
        2. User fills out the PI request form.
        3. To approve the request, NERC admin assigns the user to the PI role on KeyCloak’s user management.
        4. NERC admin approves the request and responds with a ticket reply.
        5. To remove the PI role, just reverse the step iii. And send out an email to the user informing about it.


## Manage Projects



1. **Add a new project**
    * _As a user who is a PI, I should be able to create a project by._
    * <span style="text-decoration:underline;">Steps</span>
        1. User has previously been set as a PI.
        2. User logs in to ColdFront and requests a project by going to Home → Projects and by clicking on ‘Create Project’.
        3. User requests a resource allocation on the ‘OpenShift’ resource for the above created project.
        4. Administrator approves the request.
        5. Upon approval, a project will be created in OpenShift for this particular allocation. If the user does not already exist in OpenShift the user will be created. The project created will have the following attributes
            1. Project name prefixed by a random 6 char hex
            2. Project ID / namespace as a uuid
            3. Requested quota attributes.
        6. The user will be able to authenticate using Keycloak and their institutional login.
2. **Deactivate a project or resource allocation**
    * _As an administrator, I should be able to archive any project or resource allocation and release the resources associated with it back to the pool._
    * <span style="text-decoration:underline;">Steps</span>
        1. A Coldfront admin can navigate to the project
            1. They can archive a project and expire all associated allocations by clicking ‘archive project’ by navigating to the project and clicking ‘archive project’.
            2. They can navigate to an allocation, set the status to “Denied”, and update the allocation
        2. Disabling an allocation will delete the associated OpenShift namespace, which differs from OpenStack behavior which simply disables the project.
3. **Manage a project as a PI.**
    * _As a PI, I should be able to manage and share my project with others on the team, but no one except the PI and the administrator should be able to remove the project._
    * <span style="text-decoration:underline;">Steps</span>
        1. A PI can add keycloak users to a ColdFront project under the ‘users’ section in the given project ([https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/#adding-and-removing-user-from-the-project](https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/#adding-and-removing-user-from-the-project))
        2. From here, a PI can set the user to a particular role. It seems the ‘manager’ role is the one that lets users create and remove allocations by delegating PI role/responsibilities. Some other roles should be set for other general users who are only going to use the allocated NERC resources.


## Manage Quota



1. **Set and modify quotas for projects**
    * _As an administrator of the cluster, I should be able to set and modify compute, storage and object counts quotas for any project._
    * <span style="text-decoration:underline;">Steps</span>
        1. For modifying attributes, allocation change requests can be requested by navigating to the active allocation.
        2. From here, a PI can approve the request and a call to the acct-mgt service will be made.
            1. For setting attributes, adding a new allocation attribute triggers a call to the acct-mgt service endpoint “/projects/{project_id}/quota".


## Managing Authorization Policy



1. **View and Manage Role bindings**
    * _As an administrator of the cluster, I should be able to create, view and manage role bindings for the users in the cluster._
    * <span style="text-decoration:underline;">Steps</span>
        1. After a user is added, an admin can go to the user ‘actions’ tab and set their role to ‘manager’ or ‘user’.
            1. [https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/#adding-and-removing-user-from-the-project](https://nerc-project.github.io/nerc-docs/get-started/get-an-allocation/#adding-and-removing-user-from-the-project)


## Documentation



1. **Online Documentation**
    * _As an administrator or a user, I should be able to perform any routine operations by referring to online documentation which lists the steps that need to be taken to complete an operation._
    * <span style="text-decoration:underline;">Steps</span>
        1. Administrator/user accesses documentation at:
            1. [https://nerc-project.github.io/nerc-docs/](https://nerc-project.github.io/nerc-docs/)


## Hardware Management



1. **Add and track new hardware**
    * _As an administrator of the cluster, I should be able to add nodes to the cluster. I should also be able to view all the nodes and their status._
    * <span style="text-decoration:underline;">Steps</span>
        1. Netbox
2. **Track faulty hardware**
    * _As an administrator of the cluster, I should be able to view and track the list of faulty nodes that need to be replaced._
    * <span style="text-decoration:underline;">Steps</span>
        1. Nagios or refer to notes in Netbox


## Upgrade



1. **Establish OpenShift cluster upgrade process**
    * _As an administrator of the cluster, I should be able to follow a set of documented instructions to help me in upgrading to newer versions of OpenShift. The rule book should also establish the process to mitigate any issues that might arise during the upgrade._
    * Steps
        1. See the official [OpenShift updating clusters documentation](https://docs.openshift.com/container-platform/4.10/updating/index.html) for the version of OpenShift to which you wish to upgrade.
        2. Follow the instructions to update the cluster.
    * Acceptance tests:
        1. Verify the administrator has access to the OpenShift updating clusters documentation.
        2. You can explore cluster versions and upgrades from within the Observability dashboard. For a given cluster named `nerc-ocp-prod` from version `4.10.13` to version `4.10.15` for example, [Click here to check the `from_version` of the `cluster` type record, and the `version` of the `completed` type record to ensure the versions are what you expected](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22avg%28cluster_version%7Bcluster%3D%5C%22nerc-ocp-prod%5C%22,%20type%3D~%5C%22cluster%7Ccompleted%5C%22%7D%29%20by%20%28Time,%20cluster,%20from_version,%20type,%20version%29%22%7D%5D).


## Monitoring



1. **Generate and share operations alerts**
    * _As an administrator of the cluster, I should be able to generate and share operation alerts in OpenShift using the monitoring tools available in the NERC cluster._
    * <span style="text-decoration:underline;">Steps</span>
        1. Alerts are sent to Slack
2. **Logging**
    * _As an administrator of the cluster, I should be able to track all the events in the cluster using the logging system in OpenShift._
    * <span style="text-decoration:underline;">Steps</span>
        1. [Click here to visit the Logging Grafana instance](https://logging-grafana.apps.nerc-ocp-infra.rc.fas.harvard.edu).
        2. Click on the “Explore” button which looks like a compass on the left side. At the top of that page, you can select from the dropdown the infrastructure, audit or application logs. You can then use the Log Browser to browse the different labels like kubernetes_host and select a value for a tag to filter in on actual search results. Continue to add more labels and values to narrow in on the logs you wish to see.
        3. You can build custom dashboards and alerts in this Logging Grafana instance.
3. **Monitoring and logging for the infrastructure hardware and software that is not OpenShift (for example Grafana)**
    * _As a NERC administrator, I should be able to monitor the status of any infrastructure software or hardware that supports operations for the NERC OpenShift environment, even if it is not itself part of OpenShift._
    * <span style="text-decoration:underline;">Steps</span>
        1. You can access many metrics for pods of a particular application like grafana or loki.
        2. [Click here to visit the cpu usage logs for grafana](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum_rate%7Bnamespace%3D%5C%22grafana%5C%22%7D%22%7D%5D).
        3. [Click here to visit the cpu usage logs for loki](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum_rate%7Bnamespace%3D%5C%22openshift-operators-redhat%5C%22%7D%22%7D%5D).


## Reporting



1. **Track/report usage of the cluster**
    * _As an administrator of the cluster, I should be able to view daily, weekly and monthly reports of the cluster infrastructure utilization._
    * <span style="text-decoration:underline;">Steps</span>
        1. Administrator logs into the associated XDMoD instance and views reports.
        2. [Click here to view the ACM Observability Grafana dashboards](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/). These dashboards provide insights into Control Plane Health, Optimization, Capacity, Utilization and more. You can change the timespan in the top right to show results in terms of minutes, hours, days, months or years.
2. **Track/report usage of the project**
    * _As a user and the owner of a project, I should be able to view daily, weekly and monthly reports of the infrastructure utilization by the projects I own._
    * <span style="text-decoration:underline;">Steps</span>
        1. User logs into the associated XDMoD instance and views reports for projects they own.
        2. User cannot view reports for projects they do not own. We will need to look into this, to restrict the view to only projects that they own.
        3. [Click here to view the memory usage of projects over time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22namespace:container_memory_usage_bytes:sum%22%7D%5D).
        4. [Click here to view the cpu usage of the projects over time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22node_namespace_pod_container:container_cpu_usage_seconds_total:sum%22%7D%5D).
        5. [Click here to show the projects using the top 5 cpu usage at each point in time](https://multicloud-console.apps.nerc-ocp-infra.rc.fas.harvard.edu/grafana/explore?orgId=1&left=%5B%22now-1h%22,%22now%22,%22Observatorium%22,%7B%22exemplar%22:true,%22expr%22:%22topk(5,%20(1%20-%20avg(rate(node_namespace_pod_container:container_cpu_usage_seconds_total:sum%7B%7D%5B$__rate_interval%5D))%20by%20(namespace)))%22%7D%5D).
