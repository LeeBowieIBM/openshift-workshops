# Monitoring Openshift
## Setup CRC
Monitoring is not enabled by default on CRC!!

Do all the steps in workshop1-intro EXCEPT apply the following commands before you do a ```crc start```
```
crc config set memory 16384
crc config set enable-cluster-monitoring true
```

More guidence here

https://crc.dev/crc/#starting-monitoring_gsg

https://crc.dev/crc/#configuring-the-instance_gsg

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



## References
Red Hat Docs

https://docs.openshift.com/container-platform/4.10/monitoring/monitoring-overview.html

https://docs.openshift.com/container-platform/4.10/monitoring/managing-alerts.html#managing-alerts

Excellent Blog on Monitoring in Openshift https://www.opensourcerers.org/2022/02/14/enabling-monitoring-scaling-alerting/

Good CRC Deepdive Blog https://alesnosek.com/blog/2021/02/28/deep-dive-into-codeready-containers-deployment-on-linux/

### Links to my supporting files
https://docs.google.com/presentation/d/1wuBeP0Wqyj4a3VlCXh7ddOJ5F991J_XKuwrn-QbYDlM/edit?usp=sharing
https://docs.google.com/document/d/1OwHoXV_9H78b_4KSmQ07VHdkyPVzBtne06LQZhwz8-U/edit?usp=sharing

