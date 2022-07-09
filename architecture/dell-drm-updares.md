# Updating the Dell DRM repositories

## Cutsheet

Server: <http://nerc-drm.rc.fas.harvard.edu/>

DRM Binary: /usr/bin/drm

DRM Dir: /opt/dell/dellrepositorymanager/

Repo Staging Dir: /opt/dell/dellrepositorymanager/fc430

FC430 Step Firmware Hosted Dir: /var/www/html/fc430-step (This is a custom repository to handle the step firmware, be careful if editing)

FC430 Firmware Hosted Dir: /var/www/html/fc430 (This is the main dir we'll be working with)

## Downloading latest updates from Dell

```shell
# drm -r=fc430 --update
```

-r: specify repo to update

--update: refresh firmware in repo

## Verify that only BIOS and iDRAC firmware resides in repo

```shell
# drm -r=fc430 -li=category
```

-li: list specified content type in repo

Output should like like this

```shell
[root@nerc-drm dellemcrepositorymanager]# drm -r=fc430 -li=category

Categories
----------
BIOS
iDRAC with Lifecycle Controller
```

## Remove any extra categories

If any categories are listed outside the above list remove them

```shell
# drm -r=fc430 --delete --category="<Offending Category>"
```

## Export Catalog and Firmware files

```shell
# drm --deployment-type=share --location=/opt/dell/dellemcrepositorymanager/fc430/ -r=fc430
```

--deployment-type: creates a deployment of a specific type (share gives us the Catalog.xml and the update packages)

--location: the directory to export the files to

## Move exported files to http share

DRM is weird about permission and won't export to a directory that doesn't have it's permissions set as 777

```shell
# mv /opt/dell/dellreopsitorymanager/fc430/* /var/www/html/fc430/
```
