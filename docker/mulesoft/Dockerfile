# Download base image ubuntu 20.04
FROM ubuntu:20.04

# Define environment variables.
ENV MULE_HOME /opt/mulesoft
ENV JAVA_HOME /opt/java/openjdk
# ENV LANG pt_BR.utf8

RUN mkdir -p $MULE_HOME
RUN mkdir -p $JAVA_HOME

# Update Ubuntu Software repository
RUN apt-get update

# Set locale
# RUN apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    # && localedef -i pt_BR -c -f UTF-8 -A /usr/share/locale/locale.alias $LANG

# Install packages
RUN apt-get install -y \
    bash \
    curl \
    vim

# Install JDK 8
# local file
COPY OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz /tmp
# online file
# RUN set -eux; \
#   curl /tmp/OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz https://github.com/AdoptOpenJDK/openjdk8-binaries/releases/download/jdk8u282-b08/OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz; \
#   echo "e6e6e0356649b9696fa5082cfcb0663d4bef159fc22d406e3a012e71fce83a5c */tmp/OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz" | sha256sum -c -; 

COPY ./install-openjdk /usr/local/bin/install-openjdk
RUN chmod +x /usr/local/bin/install-openjdk

RUN /usr/local/bin/install-openjdk

ENV PATH="$JAVA_HOME/bin:$PATH"

# Install Mulesoft
COPY mule-standalone-4.2.0-hf1.tar.gz /tmp

COPY ./install-mulesoft /usr/local/bin/install-mulesoft
RUN chmod +x /usr/local/bin/install-mulesoft

RUN /usr/local/bin/install-mulesoft

# Copy apps into Systen
RUN mkdir -p /tmp/apps
COPY ./apps/ /tmp/apps

# Execute Mulesoft
COPY ./mule-start /usr/local/bin/mule-start
RUN chmod +x /usr/local/bin/mule-start

CMD /usr/local/bin/mule-start

# Define mount points.
# VOLUME ["/opt/mule/logs", "/opt/mule/apps", "/opt/mule/domains", "/opt/mule/conf", "/opt/mule/patches", "/opt/mule/plugins", "/opt/mule/server-plugins", "/opt/mule/policies"]

# Define working directory.
WORKDIR /opt
# WORKDIR /opt/mulesoft

# Configure (default ports) external access:

# Mule remote debugger
# EXPOSE 5000

# Mule project port
EXPOSE 8081



# docker run -it mulesoft
# docker build -t mulesoft .