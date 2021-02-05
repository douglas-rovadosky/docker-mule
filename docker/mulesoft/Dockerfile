# Download base image ubuntu 20.04
FROM ubuntu:20.04

# Define environment variables.
ENV MULE_HOME /opt/mulesoft
ENV JAVA_HOME /opt/java/openjdk

RUN mkdir -p $MULE_HOME
RUN mkdir -p $JAVA_HOME

# Update Ubuntu Software repository
RUN apt-get update

# Install packages
RUN apt-get install -y \
    bash \
    curl

# Install JDK 8
COPY OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz /tmp

# Extract Java JDK8
RUN cd $JAVA_HOME; \
    tar -xf /tmp/OpenJDK8U-jdk_x64_linux_hotspot_8u282b08.tar.gz --strip-components=1;

# set environment variable
ENV PATH="$JAVA_HOME/bin:$PATH"

# Install Mulesoft
COPY mule-standalone-4.2.0-hf1.tar.gz /tmp

# Extract mulesoft
RUN cd $MULE_HOME; \
    tar -xf /tmp/mule-standalone-4.2.0-hf1.tar.gz --strip-components=1;

# Set environment variable
ENV PATH="$MULE_HOME/bin:$PATH"

# Copy apps into mulesoft apps
COPY ./apps $MULE_HOME/apps

# Execute Mulesoft
CMD bash $MULE_HOME/bin/mule

# Define working directory.
WORKDIR /opt/mulesoft

# Configure (default ports) external access:
# Mule project port
EXPOSE 8081