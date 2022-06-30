# Intro - Getting started with Openshift
## Get crc
If your computer has more than 10GB of RAM download “Code Ready Containers” (Openshift for your laptop) here
```
https://console.redhat.com/openshift/create/local
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

# Install a db
```
 oc new-app mariadb-ephemeral
```

# Create a wordpress db
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
