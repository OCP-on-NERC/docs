1. ## **Managing Users**
    **1.1 Terms Acceptance**
New users should be informed of the acceptable uses of the NERC OpenShift environment before they are granted any access to the environment.  This applies equally to PIs, administrators, and ordinary users.  New users should also be informed that operations data for this environment will be archived and used for research.  (Because the cluster cannot currently meet GDPR requirements for removing users' data records, users expecting or requiring GDPR protections should be notified that they should not use NERC OpenShift at this point in time.)
    **1.2 Request a new account**
- 1.2.A : As a new user from an MGHPCC consortium member University, I should be able to create an account for myself in the NERC OpenShift environment by registering into the  MGHPCC Shared Services Account Portal, also known as RegApp, to request basic NERC access.
- 1.2.B : As a new user who isn’t from any of the NERC participating organizations, I should be able to raise a ticket/issue with a reason to request a new account and I should be acknowledged when the account is approved or denied.
    **1.3 Onboard a new user**
Once successfully registering and confirming my email address by clicking the activation link, I should be able to log in and set up my OpenShift environment correctly by following the procedure(s) listed in the onboarding document.
    **1.4 Disable a user**
As an administrator, I should be able to disable a user’s account, labels associated with the user, and user identity from the cluster using KeyCloak.
    **1.5 Add/Remove PI privilege to a user**
For any user account, a NERC  administrator should be able to add or delete PI status associated with that account, and the status should be carried through to OpenShift user information. A user may be a PI on multiple projects, and projects may have multiple PIs.
    **1.6 Add/Remove administrator privilege to a user**
For any user account, an OpenShift administrator should be able to add or remove administrative privileges to that user account. (This refers to cluster administrative privileges, which are distinct from PI privileges.)  BEFORE a user receives admin privileges, they must read and acknowledge the data privacy guidelines for administrators of the NERC OpenShift environment.  (This requirement does not apply to early testing in the NERC OpenShift environment, because the guidelines are being developed in parallel with that phase of the project.)
2. # **Manage Projects**
    **2.1 Add a new self-provisioned namespace**
As a user, I should be able to create a self-provisioned namespace in the Developer view by Navigating to Home → Projects and by clicking on ‘Create Project’.
    **2.2 Deactivate a project**
As a PI of the project, I should be able to remove any project and release the resources associated with it back to the pool.
    **2.3 Add/remove a project as a PI**
As a PI, I should be able to create an OpenShift namespace associated with my identity as its PI in ColdFront.
   **2.4 Add/remove a people as a PI**
As a PI, I should be able to add additional PIs/people to my project. As a PI, I should be able to remove PIs/people from my project.
3. ## **Manage Quota**
    **3.1 Set and modify quotas for projects**
As a PI of the project, I should be able to request to set and modify compute, storage, external addresses, and object count quotas for the projects I own.
4. ## **Managing Authorization Policy**
    **4.1 View and Manage Role bindings**
As an administrator of the cluster, I should be able to create, view and manage role bindings for the users in the cluster.
5. ## **Documentation**
    **5.1 Online Documentation**
As an administrator or a user, I should be able to perform any routine operations by referring to online documentation which lists the steps that need to be taken to complete an operation.
6. ## **Hardware Management**
    **6.1 Add/Remove and track hardware**
As an administrator of the cluster, I should be able to add/remove cluster nodes. I should also be able to view all the nodes and their status.
    **6.2 Track faulty hardware**
As an administrator of the cluster, I should be able to view and track the list of faulty nodes that need to be replaced.
7. ## **Upgrade**
    **7.1 Establish OpenShift cluster upgrade process**
As an administrator of the cluster, I should be able to follow a set of documented instructions to help me in upgrading to newer versions of OpenShift. The document should also establish the process to mitigate any issues that might arise during the upgrade.
8. ## **Monitoring**
    **8.1 Generate and share operations alerts**
    - As an administrator of the cluster, I should be able to generate, view, and share operation alerts in OpenShift using the monitoring tools available in the NERC cluster and store them for 30 days.
    - Critical alerts should be automatically shared by being published to a Slack channel identified by NERC.
    - Security events and alerts should be logged and stored for 90 days.
    - Events and alerts should be archived for researchers' use.
    **8.2 Logging for OpenShift**
As an administrator of the cluster, I should be able to track all the events in the cluster using the logging system in OpenShift.
    **8.3 Monitoring and logging for the infrastructure hardware and software that is not OpenShift (for example Grafana)**
As a NERC administrator, I should be able to monitor the status of any infrastructure software or hardware that supports operations for the NERC OpenShift environment, even if it is not itself part of OpenShift.
- Storage and Network operations monitoring and alerting are currently outside the scope of these use cases.
9. ## **Reporting**
    **9.1 Track/report usage of the cluster**
As an administrator of the cluster, I should be able to view daily, weekly, and monthly reports of the cluster infrastructure utilization curated by the namespace.
10. ## **Data Management**
    **10.1** As an administrator of the cluster, I should be able to access operational logs, error messages, alerts, and other relevant data used to investigate and resolve operational issues when they are created.  I should also be able to access this information in place in the operations environment for at least 30 days following its creation.
    **10.2** As an administrator of the cluster, I should be able to access operational information that is specifically useful for security audits and investigations (e.g. records of privilege escalations, certificate changes, etc.) when it is created and for 90 days thereafter.
    **10.3** All operational data should be archived and stored securely outside the operations environment monthly.  This operations data will eventually be provided to researchers after appropriate procedures have been established for protecting any sensitive data and controlling researcher access to the data.  Current operations use cases do not call for deleting any archived data.  (Defining procedures for allowing researchers access to the archived data is outside the scope of this document.)
    **10.4** Once operations data is archived, it can be removed from the operations environment.
