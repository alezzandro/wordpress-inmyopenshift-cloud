# Openshift ready template for WordPress platform!

This repository holds an OpenShift ready template for running a wordpress platform on your OpenShift PaaS.
<br>
<a href="http://wordpress.inmyopenshift.cloud">http://wordpress.inmyopenshift.cloud</a>

## Overview
The following template will setup on your OpenShift platform a WordPress platform composed by an Apache webserver (the official wordpress container on DockerHub) and a centos-mysql container for holding back the wordpress data.<br>
Keep in mind that all the setup is stateless: mysql container is shipped with emptyDir volume, you should replace it with a persistent volume to ensure data saving.

## Requirements
This is a briefly list of the necessary requirements before trying run the template:
* Internet access (at least docker.io in whitelist) from your working OpenShift platform
* RUNASUSER field for 'restricted' Security Context Constraint (scc) set to 'RunAsAny'. This is necessary for letting WordPress official container to run as root. -> ($ <i>oc edit scc restricted</i>)

## How-to
Easy and fast deployment in few steps:
```
$ git clone https://github.com/alezzandro/wordpress-inmyopenshift-cloud.git

$ cd wordpress-inmyopenshift-cloud

$ oc create -f wordpress-openshift-template.yaml

$ oc new-app wordpress-openshift
```

## Advanced configuration
You'll find below a list of the all available fields for advanced configuration:
* NAME: The name assigned to all of the frontend objects defined in this template
* MEMORY_LIMIT: Maximum amount of memory the Wordpress container can use
* MEMORY_MYSQL_LIMIT: Maximum amount of memory the MySQL container can use
* APPLICATION_DOMAIN: The exposed hostname that will route to the Wordpress service, if left blank a value will be defaulted
* DATABASE_SERVICE_NAME: Database Service Name
* DATABASE_NAME: Database Name
* DATABASE_USER: Database User
* DATABASE_PASSWORD: Database Password
* DATABASE_ROOT_PASSWORD: Database root Password
* WORDPRESS_AUTH_KEY: Wordpress auth key
* WORDPRESS_SECURE_AUTH_KEY: Wordpress secure auth key
* WORDPRESS_LOGGED_IN_KEY: Wordpress logged in key
* WORDPRESS_NONCE_KEY: Wordpress nonce key
* WORDPRESS_AUTH_SALT: Wordpress auth salt
* WORDPRESS_SECURE_AUTH_SALT: Wordpress secure auth salt
* WORDPRESS_LOGGED_IN_SALT: Wordpress logged in salt
* WORDPRESS_NONCE_SALT: Wordpress nonce salt

<b>Please note</b>: if you don't set any of the previous fields they will be defaulted/random generated.

