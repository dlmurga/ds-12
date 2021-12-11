FROM ubuntu:20.04

ARG DEBIAN_FRONTEND=noninteractive
ARG package_folder
ARG war_folder
ARG config_folder

# Install packages
RUN apt update && \
    apt install -y default-jdk maven git && \
    rm -rf /var/lib/apt/lists/*

# Clone source code from git
WORKDIR ${package_folder}
RUN git clone https://github.com/dlmurga/MY-App42PaaS-Java-MySQL-Sample.git

# Build war file
RUN mvn package -f ${package_folder}/MY-App42PaaS-Java-MySQL-Sample/pom.xml

# Copy config file
RUN mkdir -p ${config_folder} && \
    cp ${package_folder}/MY-App42PaaS-Java-MySQL-Sample/WebContent/Config.properties \
       ${config_folder}/Config.properties

# Copy war file
RUN mkdir -p ${war_folder} && \
    cp ${package_folder}/MY-App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war \
       ${war_folder}/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war