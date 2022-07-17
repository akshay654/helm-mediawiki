# helm-mediawiki-demo
Files needed for a demo of deploying mediawiki to kubernetes

## Prerequisites
* docker
* a kubernetes cluster
* a mysql database (it's not necessary for this to be running in kubernetes)

## Instructions
* Replace the values in values.yaml if needed (keep the enableConfigmap false for first revision)
* helm install (releasename) -f values.yaml .
* Login into mysql and give db owner privileges permission to database (mediawikidb) for user (mediawiki) added in values
* After successfull deploy open the svc url (node port) in broswer and follow steps to configure local php settings and after installation download the file to your local
* Replace the file content in files/Localsettings.php with the content of files you downloaded
* Modify the value enableConfigmap = true in values.yaml
* Optionally if you want you can configure HPA in templates/hpa.yaml for scaling purpose
* For deleting - helm uninstall Release-name
