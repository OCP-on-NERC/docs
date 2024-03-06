# Observability

## Who, Why, What, When, How Often, How, Where
Goal of this document is to think about the different users and usecases for observability in this setup for NERC.
The focus will not be on a general view of all possible personas and usecases, but rather on the usecases that are most relevant to the NERC usecase.
For sure, some universal ideas will be covered and can be used as a starting point for other approaches.
Every topic should also covering musts, possible problems, what-not-to, and outlooks.

Main goal is, solving the personas problem.
Then quality, easiness, speed, and pro-active help (forecast, prevent). Depending on the definition, all the mentioned things can fall under quality.

`When there is nothing left to get rid of, to not destroy the needed solution.`

## Who
This will cover the personas
- Professor
- Student
- Accounting
- Admin for classes
- Admin for NERC
- (RH) Contributor
- Accountant IRS
- Security Officer
- do we need a finer granularity in admins? like per university?

### Summary Who - Personas and Their Needs in the OBS Cluster

#### Professor
Professors lead academic classes and are responsible for planning the budget for class costs, monitoring the progress and usage of resources by students, and ensuring resources do not exceed set quotas. They require tools for efficient management and oversight of class activities and resources. Alerts for nearing resource limits and dashboards for tracking both budgetary and academic progress are essential for them.

#### Student
Students are engaged in learning through assignments and projects, relying on access to necessary resources without the need for deep interaction with the OBS cluster. Their primary need is a stable and accessible environment that supports their academic endeavors. Minimal alerts or notifications about resource availability and system status are sufficient for their requirements.

#### Accounting
Accounting personnel are responsible for writing invoices based on the usage of resources and ensuring financial operations align with budget allocations. They need detailed reports and analytics on resource consumption for accurate billing and financial planning. Tools for predictive budgeting and cost analysis can significantly aid their work.

#### Admin for Classes
Class admins maintain the operational status of classes, manage alerts and warnings, and troubleshoot and resolve issues to keep classes running smoothly. They require advanced monitoring tools for real-time resource status and automated alerting systems for potential issues. Their role involves hands-on management of classroom resources and assisting in the quick resolution of any problems.

#### Admin for NERC
NERC admins oversee the general health and performance of all resources, focusing on the broader infrastructure rather than specific class resources. They require a global view of the system's status, including hardware, software, and network health. Comprehensive dashboards and alert systems for monitoring and predictive maintenance are essential.

#### Red Hat / Contributor
Red Hat contributors or similar roles are involved in maintaining and enhancing the OBS cluster's infrastructure, including the development of new features and dashboards. They are key to the continuous improvement of the system, requiring development and monitoring tools that support innovation and maintenance. Access to advanced analytics and customization capabilities is critical for their work. Collaboration tools for contributing to system enhancements are also crucial for their work.

#### Accountant IRS
IRS accountants are concerned with auditing and verifying the accuracy of invoicing for compliance and regulatory purposes. They need secure access to detailed resource usage and financial reports to ensure transparency and correctness in billing. Tools for audit trails and compliance verification are essential for their role; secure access controls to protect sensitive information, also.

#### Security Officer
Security officers focus on maintaining the integrity and security of the OBS cluster, preparing for audits, and responding to incidents. They require real-time security monitoring tools, access to detailed logs for investigations, and compliance tracking features. Alerts for security breaches and comprehensive reporting tools are crucial for their responsibilities.


###
### Professor
#### Problem to solve
- How many students of my class are using it?
  - Budget (paying the online bill)
  - Participation (cloud vs local deployment)
  - When are they using it ()
- Setting a budget
#### Solution
#### Trigger
- Budgetplanning
- Exams, homework, assignments
- Planning next class
- End of month accounting, bookkeeping
#### Action
#### Output
#### Quality Definition

### Student
#### Problem to solve
- creating work environents
- creating dashboards and observability
- do we need a finer granularity (different classes, different painpoints?)
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### Accounting
#### Problem to solve
- how much hours are used
- who used it
- what group/customer do they belong to
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### Admin for classes
#### Problem to solve
- certain clusters/namespaces
- certain users
- classes need to have enough resources
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### Admin for NERC
#### Problem to solve
- Status of ALL clusters
- Hardware & software
- same as RH Contributors
  - Checking new features (e.g. garbage collection for old jupyternotebooks)
  - Status after deploying new versions or upgrades
  - Status after fixing a problem
  - Regression (test) status
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### Other customers
#### Problem to solve
- how much do I have to pay
- setting a budget
- being warned (customized)
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### (RH) Contributor
#### Problem to solve
- Checking new features (e.g. garbage collection for old jupyternotebooks)
- Status after deploying new versions or upgrades
- Status after fixing a problem
- Regression (test) status
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition


## Why
This will cover the needed insight

## What
This will cover the product, used by the receiver.
Measure the quality, that can be defined by e.g.
- will it solve the problem
- how much did it help
- did it prevent a not-wanted outcome
- did it reach the right persons(s)
- did it support the outcome (easier, faster, better)

## When
This will cover the possible trigger, alerts; from the inside (treshold, limits, errors, ...) and outside(time, events, ...)

## How Often
This will cover the frequency of the alerts, separating noise from information.
Being aware of status (vital signs) as well as trends (change in values) will be important.
### Ideas:
- logarithmic scale triggering
- ISO fallback
- not too much

## How
This will cover, how someone,something will be informed.
Channels, places, dashboards, etc.

## How long
This will cover the retention time of data, information, dashboards, etc.
But it can also be about the drill up, drill down and details.

## Where
This will cover, what functions and storage can be archived with what cluster the best.

## How to react
Power is nothing without control. And alerts are nothing without action.
It is often underestimated, how important a (maybe manual) process outside the system is, and needs to be defined.
Maybe a [RACI matrix](https://www.aihr.com/blog/raci-template/) could come in handy here.

## Matrix
This should become a final matrix to easy see, what persona needs what product where and when.

| Persona | Outcome | Channel | Urgency | Cluster | Reaction |
|---------|---------|---------|---------|---------|----------|

## Usecases
A more practical approach to see the different personas and goals in action.
