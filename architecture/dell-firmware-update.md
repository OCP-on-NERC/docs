# Dell Firmware Update Automation

## Cutsheet

Playbook: <https://github.com/OCP-on-NERC/nerc-ansible/blob/main/playbooks/bios-upgrade-prod-dell.yaml>

**Dependencies**:

Python:

- omsdk
- dnspython

Ansible:

- amazon.aws
- dellemc.openmanage
- community.general

OS:

- RACADM

## Clone ansible-nerc repository

```shell
git clone git@github.com:OCP-on-NERC/nerc-ansible.git
```

## Installing dependencies

Python

```shell
pip3 install -r pip_requirements.txt
```

Ansible

```shell
ansible-galaxy install -r requirements.yaml
```

RACADM

```shell
wget https://dl.dell.com/FOLDER05920767M/1/DellEMC-iDRACTools-Web-LX-9.4.0-3732_A00.tar.gz

tar -xvzf DellEMC-iDRACTools-Web-LX-9.4.0-3732_A00.tar.gz

sudo dnf install iDRACTools/racadm/RHEL8/x86_64/*
```

## Check latest catalog file name

Browse to the FC430 http share
<http://nerc-drm.rc.fas.harvard.edu/fc430/>

Find the latest catalog file name (i.e. fc430_1.10_Catalog.xml)

## Run playbook

From the playbooks directory

```shell
ansible-playbook bios-upgrade-prod-dell.yaml  --connection=local -K --extra-vars "target_firmware_catalog=<latest catalog filename>"
```

We use ask become password and local connection because we'll be executing the dell update commands and racadm commands locally. Racadm requires super user privileges.

Example:

```shell
ansible-playbook bios-upgrade-prod-dell.yaml  --connection=local -K --extra-vars "target_firmware_catalog=fc430_1.10_Catalog.xml"
```
