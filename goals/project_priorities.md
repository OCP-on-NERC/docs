
## Goal 1: 

The first goal is to build and test a production OpenShift testbed that meets NERC needs (per second goal).  For this build, use released Red Hat and upstream open source software that has already been used in either the Operate First Smaug cluster or the OpenShift MOC cluster.  Both clusters are currently operating and supporting users (physically in the MGHPCC), which reduces risk for the production testbed.  (Depending on timing for the installation, newer versions that what has been installed in Smaug may be used for the NERC build.)  (See https://github.com/OCP-on-NERC/docs/tree/main/architecture for more information on hardware and software expected  to be used for the NERC build)   A team of Red Hat, NERC and MOC staff will build the cluster and turn it over to NERC (hardware and software) for operations and further expansion after successful completion of Operations Use Cases. 

### Assumptions:

“The cluster” refers to the production OpenShift system build-out on the NERC donated hardware.  
1. The production OpenShift cluster will be initially built and tested by the Red Hat Research group and the MOC engineering staff, working together.
2. The cluster will be physically located in the MGHPCC.  NERC donated server hardware for the initial build is located at Row 7 Pod C Cage 03 for the infra cluster and Row 7 Pod C Cage 03 (controllers) & Row 1 Pod A Cage 08 (workers) for the prod cluster and Row 7 Pod B Cage 19 for the test cluster.  Note that additional hardware in NET2 racks is not part of this deployment.   (see https://docs.google.com/document/d/1wleTt-j-EDp9Ix75mdinhbQqmlK4udMAp9BtJ6faOpY /edit for original proposal for the elastic data center.)
3. The cluster will use a public repo (https://github.com/OCP-on-NERC) for all docs, configurations, and new software that isn’t already supported in a different public repo.  (Secrets will of course not be stored in a public repo.) The project to build and operate this cluster will be a public project that is closely related to the Operate First community, and submits new code to that community wherever possible. (The Acceptable Use Policy for this project may differ from the general Operate First AUP, depending on BU/Harvard University requirements.)
4. The cluster will support university researchers (including students), as well as open source software developers.  Use cases will include providing remote computing, storage, and adequate network bandwidth to support all end users.  The exact number of users has not been forecast, but the working estimate is up to 1000. The exact number of projects is not forecast, but the working estimate is 400.   (Scaling will be addressed in the reference architecture document, not with testing at scale.)   All users are remote  and use the public Internet to access cluster resources.  Some users will also need public IP addresses for their applications/projects.  (NERC typically uses a bastion host with firewall rules to provide this.).  A rough estimate from the NERC group is that the final production cluster will need to include about 2000 cores to be adequate for the expected number of users and projects.  We expect initially one physical rack to be allocated for the production cluster in the MGHPCC, but the plan for this deployment includes only the hardware specified in assumption two.  Additional worker nodes will be added in later phases as the cluster grows.
5. Volume storage for user and operations data will be provided by NESE.  (Ceph Rados Block Device storage has been used successfully in Operate First, but Ceph File System storage has not, so we will start with just Ceph RBD.) Initial allocation for storage will be 700TB in NESE, in addition to any local storage available in the rack.   (An outstanding question exists on how to integrate with NESE, because NESE requires that CephFS is used for NESE managed DTNs because they must share the same IdP.  e.g. sets of DTNs run Globus, MinIO/S3, NET2/xrootd.)
6. During testing, the Red Hat Research group and the MOC will operate the cluster together.  All operations will be secure and remote.  (Hands-on support at MGHPCC will be needed for hardware lifecycle management.)
7. Testing will include the following work.
   1. Basic functional testing to verify the OpenShift cluster build
   2. Basic functional testing of any associated systems required to support users  or operations (e.g. research data storage, secrets management)
   3. Basic testing to verify operations use cases
      1. add new users/projects
      2. delete users/projects
      3. set/change quotas for projects
      4. add new hardware (servers, disks)
      5. replace faulty hardware (servers, disks)
      6. Upgrade OpenShift cluster (both software and OS upgrades. No hardware upgrades)
      7. generate and promptly distribute useful operations alerts
      8. respond to software alerts
      9. respond to security events
      10. track/report weekly usage
8. Operations use cases will specify whether they are manual, and/or use particular tools (e.g. ColdFront for user/project onboarding, XDMOD for usage accounting ).  NERC is the authority for documenting operations requirements for use cases according to their production requirements, but the intention for the first cluster build is to choose the minimum viable processes to support production operations on a stand-alone OpenShift cluster.
9. NERC will review all final successful tests, and either run their own additional tests (if manpower allows), or sign off on the tests as completed by MOC and Red Hat.
10. NERC will take over operations of the initial OpenShift testbed following successful acceptance test completion.

## Goal 2: 

The second goal is for NERC to support a limited number of early users and projects on the first production OpenShift Testbed.  Early users and projects should start using the cluster as soon as Acceptance testing is complete, in order to burn in as much of the system as possible before GA in fall.  Red Hat support issues will be generated as needed, and escalated with the help of Red Hat consultants and the TAM assigned to this project.   MOC and NERC will be responsible for escalating support issues with other open source software providers (e.g. ColdFront).

## Goal 3:

The third goal is for Red Hat and MOC to proceed with enhancements to support the next production OpenShift testbed expansion and the enhancements to operations use cases requested by NERC during the initial cluster build, test, and limited-user operations phases.  (There is also a desire to add ESI and ODH to the NERC OpenShift environment, but that is not part of this project plan.)