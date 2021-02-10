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

1. Design:
  - Database as a service
  - Mediawiki as a service
  
  ( Diagram uploaded)
  
  
  - Database docker image contians: ![](https://github.com/04NehaSingh/mediawiki_deployment/workflows/publish_mariadb_image/badge.svg) 
      a. mariadb-server and mysql
      
      Use: docker pull 11nehas/mariadb:latest      
  
  - mediawiki docker image contians :![](https://github.com/04NehaSingh/mediawiki_deployment/workflows/publish_mediawiki_image/badge.svg) 
      a. apache 2.4.46 verison
      b. php: 7.3.7 version
      c. mediawiki: 1.33.0 version 

      Use: docker pull 11nehas/mediawiki:latest 
