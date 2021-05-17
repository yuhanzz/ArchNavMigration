FROM ubuntu:16.04

RUN apt-get update

RUN apt-get -y install unzip

# install java
COPY jdk-8u211-linux-x64.tar.gz .
RUN tar zxvf jdk-8u211-linux-x64.tar.gz
RUN rm jdk-8u211-linux-x64.tar.gz
RUN update-alternatives --install /usr/bin/java java /jdk1.8.0_211/bin/java 1
RUN update-alternatives --set java /jdk1.8.0_211/bin/java
ENV JAVA_HOME=/jdk1.8.0_211
ENV PATH=$PATH:$JAVA_HOME/bin

# install glassfish
COPY glassfish-5.0.1.zip .
RUN unzip glassfish-5.0.1.zip
RUN rm glassfish-5.0.1.zip
ENV GF_HOME=/glassfish5
ENV PATH=$PATH:$GF_HOME/bin

# configure glassfish
COPY domain.xml glassfish5/glassfish/domains/domain1/config

# copy the adf essentials jars into the glassfish lib folder 
COPY adf-essentials.zip .
RUN mkdir adf-essentials
RUN unzip -j adf-essentials.zip -d adf-essentials
RUN mv adf-essentials/* glassfish5/glassfish/domains/domain1/lib
RUN rm -r adf-essentials

# copy the fortress security jar into the glassfish lib folder 
COPY archemy-security-1.0-SNAPSHOT-jar-with-dependencies.jar glassfish5/glassfish/domains/domain1/lib

# copy the mysql connector jar into the glassfish lib folder 
COPY mysql-connector-java-5.1.47.jar glassfish5/glassfish/domains/domain1/lib

# autodeploy archemy.ear after glassfish starts
COPY archemy.ear glassfish5/glassfish/domains/domain1/autodeploy


ENTRYPOINT ["glassfish5/glassfish/bin/asadmin", "start-domain", "--verbose"]

EXPOSE 9999 4848