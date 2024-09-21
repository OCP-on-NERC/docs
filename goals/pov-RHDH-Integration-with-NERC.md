# Point of View (POV) Document: Integrating Red Hat Developer Hub into NERC

## Overview

The NERC open cloud service, built on Red Hat OpenShift and managed through ColdFront, supports researchers, universities, professors, students, and staff. Despite its functionality, NERC's current onboarding and resource allocation processes present several challenges, including complexity, manual interventions, and scalability issues.

To address these challenges, the Red Hat Developer Hub (RHDH) is being considered for integration into NERC to provide a single pane of glass, one-click workflows, and a streamlined dashboard. This document aims to assess the feasibility of integrating RHDH, focusing on improving the user experience, enhancing automation, and providing more efficient management processes.

## Personas and Use Cases

This document focuses on three primary personas: general users, professors, and NERC admins. Other personas, such as students and assistants to professors, may be considered later.

### General Users (Mixed Technical Expertise)

* **Use Case:** Creating a project in ColdFront, requesting, approving, and allocating resources.
* **Current Workflow:** Users go through multiple steps in various tools (VPN access, ColdFront, OpenShift) for project creation and resource allocation.
* **Pain Points:** Slow onboarding, manual approvals, and scattered processes across different platforms.


### Professors (Intermediate to Advanced Technical Expertise)

* **Use Case:** Managing multiple students and classes using Red Hat OpenShift AI and handling class/project creation, homework, and exams.
* **Current Workflow:** Professors must repeat processes for each class, project, or semester. Managing multiple projects is time-consuming and not easily scalable.
**Pain Points:** Lack of automation, redundancy in managing similar projects, manual tasks, and the need to interact with different tools repeatedly.

### NERC Admins (Advanced Technical Expertise)

* **Use Case:** Maintaining NERC resources and infrastructure, managing clusters (including bare metal and multi-tenant clusters).
* **Current Workflow:** Tasks are carried out manually, especially when managing standalone and bare-metal clusters without the use of OpenShift ACM.
* **Pain Points:** Manual processes for managing standalone and bare-metal clusters, lack of streamlined automation tools, particularly in environments where OpenShift ACM is not used.

## Potential Benefits of RHDH Integration

RHDH could address the identified pain points through features like one-click workflows, template management, and integration with OpenShift. However, its feasibility hinges on specific factors for each persona:

### (all) Users

* **Before:** Users navigate multiple tools (VPN, ColdFront, OpenShift) for onboarding and resource allocation.
* **After:** RHDH could unify these processes into a single dashboard, potentially offering one-click workflows that trigger ColdFront, OpenShift, and VPN setup automatically.
* **Challenges:** Integration requires RHDH to directly connect with ColdFront, which is currently mandatory for all users. Without this connection, the impact on time savings and user experience might be minimal.

### Professors

* **Before:** Professors create classes and projects manually, repeating similar setups each time.
* **After:** RHDH could provide templates and workflows to streamline class creation and management, reducing redundant manual efforts and improving scalability. Professors would benefit from managing all projects in one tool, avoiding repeated interactions with ColdFront and OpenShift.
* **Challenges:** The success of RHDH integration depends on its ability to interface effectively with ColdFront. If ColdFront can be triggered by RHDH or vice versa, it could significantly enhance user experience and standardize resource management.

### Admins

* **Before:** Admins manually manage clusters, especially standalone and bare-metal clusters, without using OpenShift ACM. They often rely on templates and run books for setup and deployment.
* **After:** RHDH could streamline these processes using built-in workflows and status dashboards for deployment/creation. However, if HyperShift offers an intuitive user interface and built-in automation for managing these environments, RHDH's integration may become redundant.
* **Challenges:** Integrating RHDH would require significant scripting and plugin development to align with the current NERC processes. Additionally, if HyperShift provides the necessary automation and user interface, the need for RHDH integration diminishes.

## Potential Challenges and Obstacles

### ColdFront Dependency

ColdFront is a required tool for user and resource management. If RHDH cannot directly connect with ColdFront (via APIs or other mechanisms), the integration's benefits for general users and professors may be limited. The extra step of using RHDH could become redundant without improving time savings or user experience.

### Manual Approvals

Current processes in ColdFront involve manual approvals, which may be unavoidable due to formal requirements. RHDH's ability to provide alerts and manage approval workflows could be beneficial, but further exploration of ColdFront's existing approval capabilities is required.

### HyperShift as an Alternative

If HyperShift develops an intuitive user interface and built-in automation for managing standalone and bare-metal clusters, it could address the admins' needs, potentially making RHDH unnecessary.

### Customization and Complexity

RHDH integration would involve significant customization and the use of plugins to align with the current NERC processes. The feasibility of this customization needs careful evaluation.

## Success Criteria

To measure the impact of RHDH integration, the following success criteria have been identified:

1. **Reduced time required for onboarding new users**
    - Prio High
    - Success probability: low (the current process in ColdFront and manual approval is the biggest time consumer)
2. **Decreased manual intervention by admins for cluster deployment**
    - Prio Medium
    - Success probability: medium (HyperShift could be the solution here, but if we have too many special cases/unique solutions for standalone clusters, RHDH can add on start to all links and templates but will not remove most of the manual work)
3. **Improved user satisfaction or ease of use for professors managing classes**
    - Prio Medium
    - Success probability: high (switching between so many tools: RHDH can at least become the one stop for all and give a Golden Path)
4. **Enhanced workflow automation and streamlined processes for resource allocation**
    - Prio High
    - Success probability: medium (depending on the connectivity between RHDH and OpenShift, ColdFront, ACM, and Single clusters)
5. **All users: single pane of glass, better user experience by offering one platform**
    - Prio High
    - Success probability: high (this is exactly what RHDH is made for: no matter how many tools, not retired systems, workflows, or plain documentation there are, RHDH can connect them all under one hood)

## Researching Maintenance Costs

Before integrating RHDH, it's important to evaluate the (long-term) maintenance costs associated with this addition.
1. **Customization Costs**: RHDH requires plugin and script customization to align with NERC's specific use cases.
1. **Ongoing Support**: Identify the amount of continuing support that would be necessary for updates, troubleshooting, and further development of customized scripts and plugins.
1. **Comparison with Alternatives**: If HyperShift is more efficient and requires less customization, it could be the better/cheaper choice.

It can be critical to ensure that the benefits of RHDH outweigh the costs and efforts to keep the expected scaling effects.

## Conclusion

Integrating RHDH into the NERC ecosystem has the potential to streamline processes, enhance user experiences, and reduce manual interventions. However, its feasibility depends on several factors, including its ability to interface directly with ColdFront, the need for manual approval processes, and the capabilities of alternative tools like HyperShift.

For general users and professors, the integration must provide significant time savings and a simplified user experience to be worthwhile. For admins, RHDH must demonstrate enhanced automation and ease of cluster management, especially in scenarios where OpenShift ACM is not used, and HyperShift's user interface and built-in features fall short.

The next steps include:

* Exploring ColdFront's API capabilities.
* Evaluating the necessity of manual approvals.
* Exploring HyperShift's capabilities.
* Assessing whether RHDH's integration can deliver the desired automation and usability improvements.
* Researching maintenance costs.

Based on these findings, a decision can be made regarding the implementation of RHDH within NERC.

## New ideas / Open topics / To discuss

*  Call Tom/Thor
    * ACM integration of RHDH is not yet ready, but interest and first steps
    * In general, a single cluster is not a problem; multicluster is a problem
    * Authentication: RHDH can forward tokens, but some systems (Red Hat OpenShift) are not designed to accept those
        * Single cluster: by hack/ workaround
        * Multicluster is a problem
*  Thor, personal thoughts
    * If it is about one single pane of glass/ look&feel of one platform, RHDH is a good solution
        * And if it is only a collection of the right tutorials and links for certain usecases and roles
        * In general RHDH is a mixture of docs, flows, links, status/dashboards, plugins, and own plugins/solutions
        * Especially when you have different (single job) applications or applications you can not get rid of, RHDH can at least give the easiness and feeling of one platform
    * If it is about saving time
        * For admins and professors: possible
            * admins: depending on hypershift
            * admins: yes, having all templates and playbooks in one place and maybe even adding automation/buttons/workflows
            * professors: yes, with more than one class and multiple images/semesters with the same settings
        * For basic onboarding: coldfront and the approval process so far is pretty manual and is the most delay
    * If it is about user experience: depends
        * Current users, already working with the tools (ColdFront, OpenShift, RHOAI): maybe not, adding another/ new tools
        * New users: most likely, all in one place, even the manual tutorials
