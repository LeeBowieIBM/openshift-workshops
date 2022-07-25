# Openshift in the Cloud
## Spin up a free OpenShift instance
https://developers.redhat.com/developer-sandbox/get-started

## Go into the instance WebUi
Your URL will look like this
https://console-openshift-console.apps.sandbox-m2.ll9k.p1.openshiftapps.com/topology/ns/guitargodlee-dev?view=graph

Take a look around!

# Open a terminal in the WebUi
Ya, you heard right

Click the terminal icon (>_) in the top right of the WebUi


# Check your tools and status
type ```help``` to see what CLI tools are pre-installed

```
oc status
```
# Install a Database app for Wordpress
```
 oc new-app mariadb
```

You can do it from the WebUi like this

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

# What’s it’s URL to the Wordpress admin sit?
```
oc get routes
```

# Test the Wordpress site (the one the users see)
Open the URL in a browser or click the link in topology view

