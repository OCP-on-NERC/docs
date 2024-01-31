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
- do we need a finer granularity in admins? like per university?

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
-
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition

### Admin for NERC
#### Problem to solve
- all clusters
- hardware & software
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
#### Solution
#### Trigger
#### Action
#### Output
#### Quality Definition


## Why
This will cover the needed insiggtr

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
