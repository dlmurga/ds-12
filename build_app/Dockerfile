FROM ubuntu:20.04
ARG DEBIAN_FRONTEND=noninteractive
ARG package_folder
ARG war_folder

# Install packages
RUN apt update && \
    apt install -y default-jdk maven git && \
    rm -rf /var/lib/apt/lists/* \

# Clone source code from git
WORKDIR ${package_folder}
RUN git clone https://github.com/shephertz/App42PaaS-Java-MySQL-Sample

# Build war file
RUN mvn package -f ${package_folder}/App42PaaS-Java-MySQL-Sample/pom.xml

# Copy war file
RUN cp ${package_folder}/App42PaaS-Java-MySQL-Sample/target/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war \
       ${war_folder}/App42PaaS-Java-MySQL-Sample-0.0.1-SNAPSHOT.war