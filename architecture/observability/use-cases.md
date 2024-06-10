# Observability

## Who, Why, What, When, How Often, How, Where
This document aims to outline the different users and use cases for observability in the setup for NERC.
The focus will be on the most relevant personas and use cases for NERC, though some universal ideas will be covered and can be used as a starting point for other approaches.
Each topic should also cover musts, potential problems, what-not-to-do, and outlooks.

The main goals include solving the personas' problems with quality, ease, speed, and proactive help (forecast, prevent).
Depending on the definition, all the mentioned factors can fall under quality.

"When nothing is left to get rid of, not to destroy the needed solution."

## Who
This section will cover the personas:
- Professor
- Student
- Accounting
- Admin for classes
- Admin for NERC
- (RH) Contributor
- Accountant IRS
- Security Officer
- Do we need finer granularity in admins? Like per university?

### Summary of Personas and Their Needs in the OBS Cluster

#### Professor
Professors lead academic classes and are responsible for planning budgets for class costs, monitoring the progress and usage of resources by students, and ensuring resources do not exceed set quotas.
They require tools for efficient management and oversight of class activities and resources.
Alerts for nearing resource limits and dashboards for tracking both budgetary and academic progress are essential.

#### Student
Students are engaged in learning through assignments and projects, relying on access to necessary resources without needing deep interaction with the OBS cluster.
Their primary need is a stable and accessible environment that supports their academic endeavors.
Minimal alerts or notifications about resource availability and system status are sufficient.

#### Accounting
Accounting personnel are responsible for writing invoices based on resource usage and ensuring financial operations align with budget allocations.
They need detailed reports and analytics on resource consumption for accurate billing and financial planning.
Tools for predictive budgeting and cost analysis can significantly aid their work.

#### Admin for Classes
Class admins maintain the operational status of classes, manage alerts and warnings, and troubleshoot and resolve issues to keep classes running smoothly.
They require advanced monitoring tools for real-time resource status and automated alerting systems for potential issues.
Their role involves hands-on management of classroom resources and quick resolution of any problems.

#### Admin for NERC
NERC admins oversee the general health and performance of all resources, focusing on the broader infrastructure rather than specific class resources.
They require a global view of the system's status, including hardware, software, and network health.
Comprehensive dashboards and alert systems for monitoring and predictive maintenance are essential.

#### Red Hat / Contributor
Red Hat contributors or similar roles are involved in maintaining and enhancing the OBS cluster's infrastructure, including developing new features and dashboards.
They require development and monitoring tools that support innovation and maintenance.
Access to advanced analytics and customization capabilities is critical, as are collaboration tools for contributing to system enhancements.

#### Accountant IRS
IRS accountants audit and verify the accuracy of invoicing for compliance and regulatory purposes.
They need secure access to detailed resource usage and financial reports to ensure transparency and correctness in billing.
Tools for audit trails and compliance verification, along with secure access controls to protect sensitive information, are essential.

#### Security Officer
Security officers focus on maintaining the integrity and security of the OBS cluster, preparing for audits, and responding to incidents.
They require real-time security monitoring tools, access to detailed logs for investigations, and compliance tracking features.
Alerts for security breaches and comprehensive reporting tools are crucial for their responsibilities.

### Detailed Persona Descriptions

#### Professor
- **Problem to solve:**
  - How many students are using my class resources?
  - Budget (paying the online bill)
  - Participation (cloud vs local deployment)
  - Usage patterns (when are they using it)
  - Setting a budget
- **Solution:** Tools for tracking resource usage and budgeting
- **Trigger:** Budget planning, exams, homework, assignments, planning next class, end of month accounting
- **Action:** Monitor and adjust resource allocations
- **Output:** Budget and resource usage reports
- **Quality Definition:** Accuracy in resource tracking, ease of use, proactive alerts

#### Student
- **Problem to solve:**
  - Creating work environments
  - Creating dashboards and observability
  - Differentiating needs for different classes
- **Solution:** Stable and user-friendly environments with minimal necessary interaction
- **Trigger:** Assignment deadlines, project milestones
- **Action:** Utilize resources for academic work
- **Output:** Completed assignments and projects
- **Quality Definition:** Accessibility, stability, minimal disruptions

#### Accounting
- **Problem to solve:**
  - Tracking resource usage hours
  - Identifying users and their respective groups or customers
- **Solution:** Detailed reports and analytics on resource consumption
- **Trigger:** End of billing cycles, budget reviews, financial audits
- **Action:** Generate and review resource consumption reports
- **Output:** Invoices, budget reports
- **Quality Definition:** Accuracy in billing, alignment with budget allocations

#### Admin for Classes
- **Problem to solve:**
  - Ensuring specific clusters/namespaces have enough resources
  - Managing resource allocation for certain users
- **Solution:** Advanced monitoring tools for real-time resource status
- **Trigger:** Class schedules, resource usage peaks
- **Action:** Allocate and reallocate resources as needed
- **Output:** Optimized resource allocation, minimal disruption in classes
- **Quality Definition:** Efficiency in resource management, minimal downtime

#### Admin for NERC
- **Problem to solve:**
  - Monitoring status of all clusters
  - Managing hardware and software health
  - Checking new features (e.g., garbage collection for old Jupyter notebooks)
  - Assessing status after deploying new versions or upgrades
  - Monitoring status after fixing a problem
  - Regression (test) status
- **Solution:** Comprehensive dashboards and alert systems
- **Trigger:** New deployments, system updates, detected issues
- **Action:** Monitor system health, implement fixes, and enhancements
- **Output:** System health reports, issue resolution documentation
- **Quality Definition:** System stability, proactive maintenance

#### Other Customers
- **Problem to solve:**
  - Understanding payment responsibilities
  - Setting and managing budgets
  - Receiving customized warnings
- **Solution:** User-friendly budgeting tools and customizable alert systems
- **Trigger:** Budget reviews, approaching spending limits
- **Action:** Monitor expenses, adjust budgets
- **Output:** Budget reports, alerts
- **Quality Definition:** Financial clarity, proactive budget management

#### (RH) Contributor
- **Problem to solve:**
  - Checking new features (e.g., garbage collection for old Jupyter notebooks)
  - Assessing status after deploying new versions or upgrades
  - Monitoring status after fixing a problem
  - Regression (test) status
- **Solution:** Advanced analytics and customization tools
- **Trigger:** New feature deployments, system updates, detected issues
- **Action:** Develop and implement new features, monitor system health
- **Output:** Feature deployment reports, system health reports
- **Quality Definition:** Continuous improvement, system innovation

## Why
This will cover the needed insight:
- To understand resource usage patterns
- To ensure budget compliance
- To improve system performance and reliability
- To maintain security and compliance
- To provide proactive support and problem prevention

## What
This will cover the product, used by the receiver.
Measure the quality, which can be defined by:
- Will it solve the problem?
- How much did it help?
- Did it prevent an unwanted outcome?
- Did it reach the right person(s)?
- Did it support the outcome (easier, faster, better)?

## When
This will cover the possible triggers and alerts; from the inside (thresholds, limits, errors) and outside (time, events).

## How Often
This will cover the frequency of the alerts, separating noise from information.
Being aware of status (vital signs) as well as trends (change in values) will be important.
### Ideas:
- Logarithmic scale triggering
- ISO fallback
- Not too much

## How
This will cover how someone or something will be informed.
Channels, places, dashboards, etc.

## How long
This will cover the retention time of data, information, dashboards, etc.
It can also address the drill-up, drill-down, and details.

## Where
This will cover what functions and storage can be archived with what cluster the best.

## How to React
Power is nothing without control, and alerts are nothing without action.
It is often underestimated how important a (maybe manual) process outside the system is, and it needs to be defined.
A [RACI matrix](https://www.aihr.com/blog/raci-template/) could come in handy here.

## Matrix
This should become a final matrix to easily see what persona needs what product, where, and when.

| Persona         | Outcome                                | Channel          | Urgency  | Cluster        | Reaction                  |
|-----------------|----------------------------------------|------------------|----------|----------------|---------------------------|
| Professor       | Budget and resource usage reports      | Dashboard, Email | High     | Class-specific | Adjust resource allocation|
| Student         | Completed assignments and projects     | Dashboard        | Medium   | Class-specific | Continue academic work    |
| Accounting      | Invoices, budget reports               | Email, Reports   | High     | Central        | Generate invoices         |
| Admin for Classes| Optimized resource allocation         | Dashboard, Alerts| High     | Class-specific | Manage resources          |
| Admin for NERC  | System health reports                  | Dashboard, Alerts| High     | Global         | Maintain system health    |
| RH Contributor  | Feature deployment and system health reports | Collaboration tools, Dashboard | High | Development  | Implement features and fixes |
| Accountant IRS  | Compliance and audit reports           | Secure Reports   | High     | Central        | Verify


# Use Cases for Observability Personas

## Professor
### Use Case 1: Budget Monitoring
- **Scenario:** A professor needs to ensure that the class budget is not exceeded by tracking resource usage.
- **Trigger:** Monthly budget review or nearing the end of the semester.
- **Action:** Access the dashboard to monitor current resource usage against the budget.
- **Outcome:** Adjust resource allocations or request additional budget if necessary.

### Use Case 2: Student Participation Tracking
- **Scenario:** A professor wants to track the participation of students in using cloud resources.
- **Trigger:** Weekly participation check or before major assignments.
- **Action:** Review reports on student activity and resource usage.
- **Outcome:** Identify students who need additional support or resources.

## Student
### Use Case 1: Environment Setup
- **Scenario:** A student needs to set up a working environment for a new assignment.
- **Trigger:** Assignment release or project start.
- **Action:** Use the provided tools to create a new environment and allocate necessary resources.
- **Outcome:** A stable and ready-to-use environment for academic work.

### Use Case 2: Dashboard Creation
- **Scenario:** A student needs to create a dashboard to monitor their project's progress and resource usage.
- **Trigger:** Start of a new project or ongoing project monitoring.
- **Action:** Configure a dashboard with relevant metrics and alerts.
- **Outcome:** Real-time visibility into project status and resource usage.

## Accounting
### Use Case 1: Invoice Generation
- **Scenario:** The accounting department needs to generate invoices based on resource usage.
- **Trigger:** End of the billing cycle.
- **Action:** Access detailed usage reports and generate corresponding invoices.
- **Outcome:** Accurate and timely invoices sent to respective departments or students.

### Use Case 2: Budget Forecasting
- **Scenario:** Accounting needs to forecast future budget requirements based on current usage trends.
- **Trigger:** Quarterly budget planning.
- **Action:** Analyze resource usage trends and predict future needs.
- **Outcome:** Informed budget allocations for upcoming periods.

## Admin for Classes
### Use Case 1: Resource Allocation
- **Scenario:** Class admins need to ensure that all classes have sufficient resources.
- **Trigger:** Start of a new class or detected resource shortage.
- **Action:** Monitor real-time resource status and allocate additional resources as needed.
- **Outcome:** Classes run smoothly without resource shortages.

### Use Case 2: Issue Resolution
- **Scenario:** An issue arises that affects the availability of resources for a class.
- **Trigger:** Alerts or reports of resource issues.
- **Action:** Investigate and resolve the issue promptly.
- **Outcome:** Minimized disruption to class activities.

## Admin for NERC
### Use Case 1: System Health Monitoring
- **Scenario:** NERC admins need to monitor the overall health of the system.
- **Trigger:** Regular health checks or detected anomalies.
- **Action:** Use dashboards to monitor hardware, software, and network status.
- **Outcome:** Proactive maintenance and issue prevention.

### Use Case 2: Feature Deployment
- **Scenario:** A new feature is deployed in the system, and its impact needs to be assessed.
- **Trigger:** Post-deployment phase.
- **Action:** Monitor the system for any issues or performance changes.
- **Outcome:** Successful integration of the new feature with minimal disruption.

## Red Hat / Contributor
### Use Case 1: Feature Development
- **Scenario:** Contributors are developing a new feature for the OBS cluster.
- **Trigger:** Development phase.
- **Action:** Use advanced analytics and customization tools to develop and test the feature.
- **Outcome:** High-quality feature ready for deployment.

### Use Case 2: System Enhancement
- **Scenario:** Enhancements to existing features need to be made based on user feedback.
- **Trigger:** User feedback or identified performance issues.
- **Action:** Collaborate using development tools to implement and test enhancements.
- **Outcome:** Improved system performance and user satisfaction.

## Accountant IRS
### Use Case 1: Compliance Audit
- **Scenario:** IRS accountants need to verify compliance of invoicing and resource usage.
- **Trigger:** Scheduled audit period.
- **Action:** Access secure and detailed usage and financial reports.
- **Outcome:** Verified compliance with regulatory standards.

### Use Case 2: Financial Reporting
- **Scenario:** Detailed financial reports are needed for regulatory purposes.
- **Trigger:** End of fiscal year or audit requests.
- **Action:** Generate and review comprehensive financial reports.
- **Outcome:** Accurate financial reporting for regulatory compliance.

## Security Officer
### Use Case 1: Security Incident Response
- **Scenario:** A security breach or incident is detected.
- **Trigger:** Real-time security alerts.
- **Action:** Investigate the incident using detailed logs and monitoring tools.
- **Outcome:** Mitigated security threat and documented incident resolution.

### Use Case 2: Compliance Tracking
- **Scenario:** Security officers need to ensure ongoing compliance with security standards.
- **Trigger:** Regular compliance checks.
- **Action:** Monitor compliance status and generate reports.
- **Outcome:** Continuous compliance with security policies and standards.
