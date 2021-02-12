----------------------------------------------------------------------------------------------------------------------------------------
                                          # Mediawki_deployment
-----------------------------------------------------------------------------------------------------------------------------------------
                            
Requirement:
1. Database: In this we used mariadb
2. Apache: This is used for Running the Mediawiki server 
3. PHP: For running mediawiki application and it should be (>= 5.5) 
4. Mediawiki: MediaWiki is a free and open-source wiki application written in PHP

The installation method on a single server is mentioned in https://www.digitalocean.com/community/tutorials/how-to-install-mediawiki-on-centos-7 
Deploying in cloud should be designed in the form of microservice architecture.

Design
-------
  - Database as a service
  - Mediawiki as a service
  
  ![](https://github.com/04NehaSingh/mediawiki_deployment/workflows/publish_mariadb_image/badge.svg) 
  - Database docker image contians: 
      a. mariadb-server and mysql
      
      Use: docker pull 11nehas/mariadb:latest      
  
  ![](https://github.com/04NehaSingh/mediawiki_deployment/workflows/publish_mediawiki_image/badge.svg)
  - mediawiki docker image contians : 
      a. apache 2.4.46 verison
      b. php: 7.3.7 version
      c. mediawiki: 1.33.0 version 

      Use: docker pull 11nehas/mediawiki:latest 

This repository contains:
--------------------------- 
  1. Mediawiki docker image
  2. Mariadb docker image
  3. K8s manifest file for deployment
  4. Deployment Helm charts
  5. Images
  
Deployment using K8s manifest:
------------------------------
    Kubectl apply -k ./k8s

Deployment using helm:
---------------------
    Dry-run
        helm install --dry-run --debug mediawiki --set mariadb.cred.dbname=<secret.dbname>,mariadb.cred.dbpassword=<secret.dbpass>,mariadb.cred.dbrootpassword=<secret.dbrootpass>,mariadb.cred.dbuser=<secret.dbuser> ./mediawiki_chart

    Install:
        helm install mediawiki--set mariadb.cred.dbname=<secret.dbname>,mariadb.cred.dbpassword=<secret.dbpass>,mariadb.cred.dbrootpassword=<secret.dbrootpass>,mariadb.cred.dbuser=<secret.dbuser> ./mediawiki_chart
 
How to access the service:
--------------------------
        access use: http://<service fqdn>:30163/
    
    ex: http://<service_name>.<namespace>.svc.cluster.local:30163