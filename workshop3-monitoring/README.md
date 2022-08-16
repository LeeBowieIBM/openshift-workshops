# Monitoring Openshift
## Setup CRC
Do all the steps in workshop1-intro EXCEPT apply the following commands before you do a ```crc start```
```
crc config set memory 16384
crc config set enable-cluster-monitoring true
```
Monitoring is not enabled by default on CRC
## Check your the app as kubeadmin
### Let's check out some metrics as an administrator

Administrator > Home > Overview > Cluster utilization

Administrator > Observe > Dashboards

### Let's check out what a developer sees 
Developer > Topology > wordpress > Observe

Developer > Observe

## Create an alert for all cluster level notifications
Administrator > Administration > Cluster settings > Configuration > Alertmanager 

### Setup Slack as a receiver
goto https://api.slack.com/apps?new_app=1 and create one from scratch. Don't worry it's easy!

Enable webhooks and grab the URL

Detailed instructions here https://cloud.redhat.com/blog/how-to-integrate-openshift-namespace-monitoring-and-slack

Cool kids will want Mattermost or Rocket.Chat
They can use webhooks
### Enter the info in Openshift
Test it!

Go into Slack and see if it worked.

## Create an alert as a developer for your app
