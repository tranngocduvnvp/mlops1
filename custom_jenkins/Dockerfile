# Use a Jenkins image as base image
FROM jenkins/jenkins:lts

# Install Docker using the official script
USER root
RUN apt-get update -y && \
    apt-get install -y curl && \
    curl -fsSL https://get.docker.com -o get-docker.sh && \
    sh get-docker.sh

# Configure Docker to run as a non-root user
RUN usermod -aG docker jenkins

# Enable DinD
RUN mkdir -p /var/lib/docker
VOLUME /var/lib/docker
RUN curl -sfL https://raw.githubusercontent.com/aquasecurity/trivy/main/contrib/install.sh | sh -s -- -b /usr/local/bin v0.18.3
RUN apt update -y
RUN apt install -y python3 python3-pip curl
RUN ln -s /usr/bin/python3 /usr/bin/python