# OCP on NERC Network Overview

## VLAN Assignments

| VLAN ID | Address range  | Description               |
|---------|----------------|---------------------------|
| 2170    | 10.30.0.0/22   | OBM/IPMI network          |
| 2171    | 10.30.4.0/24   | Network device management |
| 2172    | 10.30.6.0/23   | PROD baremetal network    |
| 2173    | 10.30.10.0/23  | PROD storage backend      |
| 2174    | 10.30.8.0/24   | TEST baremetal network    |
| 2175    | 10.30.12.0/24  | TEST storage backend      |
| 2176    | 10.30.9.0/24   | INFRA baremetal network   |
| 2177    | 10.30.13.0/24  | INFRA storage backend     |
| 2178    | 199.94.61.0/24 | Public network            |

## Hostnames and reserved addresses

### Infra cluster

- `api.nerc-ocp-infra1.<something>`
- `apps.nerc-ocp-infra1.<something>`

### Production cluster

- `api.nerc-ocp-prod1.<something>`
- `apps.nerc-ocp-prod1.<something>`

### Test cluster

- `api.nerc-ocp-test1.<something>`
- `apps.nerc-ocp-test1.<something>`
