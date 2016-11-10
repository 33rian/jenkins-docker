FROM jenkins:2.19.2
MAINTAINER Ta Dat <ttdat1@gmail.com>

USER root
RUN mkdir /var/log/jenkins
RUN mkdir /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN chown -R jenkins:jenkins /var/cache/jenkins

# Copy in the Docker certs, we'll use /usr/local/etc for them
COPY certs/ca-key.pem /usr/local/etc/jenkins/certs/ca-key.pem
COPY certs/ca.pem /usr/local/etc/jenkins/certs/ca.pem
COPY certs/cert.pem /usr/local/etc/jenkins/certs/cert.pem
COPY certs/key.pem /usr/local/etc/jenkins/certs/key.pem

# Make sure cert permissions are set correctly
RUN chmod +r /usr/local/etc/jenkins/certs/ca.pem
RUN chmod +r /usr/local/etc/jenkins/certs/cert.pem
RUN chown -R jenkins:jenkins /usr/local/etc/jenkins

COPY plugins.sh /usr/local/bin/custom-plugins.sh
RUN chmod +x /usr/local/bin/custom-plugins.sh
COPY resolv.conf /etc/resolv.conf

USER jenkins

ENV JAVA_OPTS="-Xmx8192m"

# Not compatible with Jenkins 2 yet, so comment out
# ENV JENKINS_OPTS="--handlerCountStartup=100 --handlerCountMax=300"
ENV JENKINS_OPTS="--logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war"

# Install default plugins
COPY plugins.txt /tmp/plugins.txt
RUN /usr/local/bin/custom-plugins.sh /tmp/plugins.txt