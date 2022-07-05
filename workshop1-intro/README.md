# Intro - Getting started with Openshift
## Get a Red Hat account
This workshop requires that you have a Red Hat account.

Create a “Personal” (not “Corporate”) account here…
```
https://www.redhat.com/wapps/ugc/register.html
```
## Get Code Ready Containers (CRC)
If your computer has more than 10GB of RAM download “Code Ready Containers” (Openshift for your laptop) here...
```
https://console.redhat.com/openshift/create/local
```

If you computer has less than 10GB RAM, or have less than 40GB of disk space, create a free Openshift cluster, before the workshop, here…
```
https://developers.redhat.com/developer-sandbox/get-started
```
## Install CRC	
 ```
 crc setup
```

## Start CRC
 ```
 crc start
 ```

# Login and check status
```
oc login -u developer https://api.crc.testing:6443
oc status
```

# Create a project 
```
oc new-project wordpress
```

# Check some stuff
```
oc status
```

# Go into the web portal
```
https://console-openshift-console.apps-crc.testing/
```

# Some OCP lingo
 Projects
 
 Apps
 
 Topology

# Install a Database app for Wordpress
```
 oc new-app mariadb-ephemeral
```

# Create a Wordpress db for Wordpress
Go into the terminal for the mariadb pod
```
mysql -u root
create database wordpress
```

# Install WordPress
```
oc new-app php~https://github.com/wordpress/wordpress
```

# Track install progress
```
oc logs -f dc/wordpress
```

# Expose the wordpress web service
```
oc expose svc/wordpress
```

# What’s it’s URL?
```
oc get routes
```

# Test it
# Add some pods
# Shut down Openshift
```
crc stop
```
# Delete everything in Openshift
```
crc delete
```
## Links
Original GDoc
https://docs.google.com/document/d/1OwHoXV_9H78b_4KSmQ07VHdkyPVzBtne06LQZhwz8-U/edit?usp=sharing

Slide Deck
https://docs.google.com/presentation/d/15b6Z_sbARKKOQ05uTuqvUm_3OZrzwK17wGttdmMcAFs/edit?usp=sharing

