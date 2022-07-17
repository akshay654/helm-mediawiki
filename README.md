# helm-mediawiki-demo
Files needed for a demo of deploying mediawiki to kubernetes

## Prerequisites
* docker
* a kubernetes cluster
* a mysql database

## Instructions
* Replace the values in values.yaml (keep the enableConfigmap false for first revision)
* Fill the mysql section in values.yaml and give root user and password and the database name - this step creates post deployment job to grant privileges on DB
* helm install <releasename> -f values.yaml . -n <namespace>
* After successfull deploy open the svc url (node port) in broswer and follow steps to configure local php settings (fill the values as specified in values.yaml for mysql host take service name in k8s)and after installation download the file to your local
* Replace the file content in files/Localsettings.php in your helm chart directory with the content of files you downloaded
* Modify the value enableConfigmap = true in values.yaml and perform helm upgrade <releasename> -f values.yaml . -n <namespace>
* Optionally if you want you can configure HPA in values.yaml (set enabled=true) for scaling purpose (Metric CPU utilization)
* For deleting - helm uninstall <releasename> -n <namespace>
