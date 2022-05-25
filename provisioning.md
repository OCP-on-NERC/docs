## Provisioning Host/DHCP server:

For hardware provisioning over PXE, the host `nerc-bootstrap.rc.fas.harvard.edu` provides:

- DHCP via `dnsmasq` (for all NERC OpenShift networks)
- TFTP
- `httpd` for serving provisioning images

This host is managed via CI/CD through an internal repository:

- https://gitlab-int.rc.fas.harvard.edu/nerc/nerc-ansible

The NERC folks are open to moving that repository somewhere public if necessary, but it will require some prep work in order to ensure that any secrets have been removed.

If folks need to make changes on the provisioning server other than manual edits to the images/isos directory then a merge request needs to be submitted, reviewed, and approved. Please ping a NERC admin if you need this and we can quickly grant access to that repo.

## Images/ISOs

The assisted installer discovery isos/images for OpenShift need to be unpacked here if you plan to PXE boot from nerc-bootstrap:

- `/srv/pxe/httpboot/openshift-discovery-iso`

The convention is:

- `/srv/pxe/httpboot/openshift-discovery-iso/<cluster>/<ocp_version>/`

The iPXE config for openshift on nerc-bootstrap expects the iso/image to be unpacked like so:

```
$ ls /srv/pxe/httpboot/openshift-discovery-iso/nerc-ocp-prod/4.10.10/

config.ign  discovery_image_nerc-ocp-prod.iso  images
```

There is a script that you can use to extract the iso once you put it in the target directory, e.g.:

```
$ bash /srv/repos/boot-openshift-ai/extract-iso.sh discovery_image_nerc-ocp-prod.iso
```

The current iPXE config for nerc-ocp-prod hosts:

```
kernel --timeout 60000 http://10.255.0.30/openshift-discovery-iso/nerc-ocp-prod/4.10.10/images/vmlinuz initrd=main ignition.config.url=http://10.255.0.30/openshift-discovery-iso/nerc-ocp-prod/4.10.10/config.ign coreos.live.rootfs_url=http://10.255.0.30/openshift-discovery-iso/nerc-ocp-prod/4.10.10/images/rootfs.img random.trust_cpu=on rd.luks.options=discard ignition.firstboot ignition.platform.id=metal console=tty1 console=ttyS0,115200n8 coreos.inst.persistent-kargs="console=tty1 console=ttyS0,115200n8"  || goto retry_boot

initrd --name main --timeout 60000 http://10.255.0.30/openshift-discovery-iso/nerc-ocp-prod/4.10.10/images/initrd.img || goto retry_boot

initrd --name root --timeout 60000 http://10.255.0.30/openshift-discovery-iso/nerc-ocp-prod/4.10.10/images/rootfs.img || goto retry_boot
```

If we need to change the iPXE configs that needs to be done via a merge request to the nerc-ansible repo that controls the deployment of the `nerc-bootstrap.rc.fas.harvard.edu` host.
