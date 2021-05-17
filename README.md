# ArchNavMigration

## Fortress
/Fortress contains all the files for building the docker image.
Original repo: https://github.com/skyline220/tomcatdocker 

## ArchNav
/ArchNav contains all the files for building the docker image.
Large files like archemy.ear needs to be retrieved using git lfs

## MySQL
/MySQL contains the modified DatabaseImport.sql that is compatible with AWS RDS with MySQL engine 8.19.

## LDAP
The ApacheDS image used is https://hub.docker.com/r/itzg/apacheds/

## Kubernetes
/Kubernetes contains the yaml files used for AWS EKS. 