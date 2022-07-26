# Openshift in the Cloud
## Spin up a free OpenShift instance
https://developers.redhat.com/developer-sandbox/get-started

NOTE: The free Openshift cluster from Red Hat Developer has many limitations! You only get one pre-defined project. You can't create additional users. It will aggressively shut down pods to save resources, etc. On the up side it comes with a bunch of installed goodies that typically you would have to add-on, like a terminal! I love me some terminal.

## Go into the instance WebUi
Your URL will look like this
https://console-openshift-console.apps.sandbox-m2.ll9k.p1.openshiftapps.com/topology/ns/```YOUR USER ID```-dev?view=graph

Take a look around!

# Open a terminal in the WebUi
Ya, you heard right

Click the terminal icon (>_) in the top right of the WebUi


# Check your tools and status
type ```help``` to see what CLI tools are pre-installed
try one!
```
oc status
```
# Install a Database app for Wordpress
```
 oc new-app mariadb
```

NOTE: We're not doing the -ephemeral version on mariadb that we used in the first workshop.
 
You can also do it from the WebUi like by right clicking in Topology > Add to Project

# Create a Wordpress db for Wordpress
Go into the terminal for the mariadb pod

Developer > Topology > mariadb > Pods > Select running pod > Terminal

```mysql -u root```
```sql
show databases;
select user from mysql.user;
create database wordpress
```

# Install WordPress via Source to Image

## What's S2I?
check their code and great description!
https://github.com/openshift/source-to-image

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

# What’s it’s URL to the Wordpress admin sit?
```
oc get routes
```

# Test the Wordpress site (the one the users see)
Open the URL in a browser or click the link in topology view

# Create a user account
```oc create user lee```
Guess what.. free Openshift won't let you do it. CRC or OCPaaS will.
more details here https://docs.openshift.com/container-platform/4.10/cli_reference/openshift_cli/developer-cli-commands.html#oc-create-user

# Create a backup of your project
There are many ways to do this.
## From the command line 
you can create a Custom Resource and schedule it
https://docs.openshift.com/container-platform/4.10/backup_and_restore/application_backup_and_restore/backing_up_and_restoring/backing-up-applications.html#oadp-scheduling-backups_backing-up-applications
## From the GUI
Hit the Export button when a Developer looking at the Topology

# Shutdown your cluster
From a terminal with access to the cluster
```$ for node in $(oc get nodes -o jsonpath='{.items[*].metadata.name}'); do oc debug node/${node} -- chroot /host shutdown -h 1; done``
more details here https://docs.openshift.com/container-platform/4.10/backup_and_restore/graceful-cluster-shutdown.html#graceful-shutdown-cluster

