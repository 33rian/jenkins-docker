FROM jenkins:2.19.2
MAINTAINER Ta Dat <ttdat1@gmail.com>

USER root
RUN mkdir /var/log/jenkins
RUN mkdir /var/cache/jenkins
RUN chown -R jenkins:jenkins /var/log/jenkins
RUN chown -R jenkins:jenkins /var/cache/jenkins
USER jenkins

ENV JAVA_OPTS="-Xmx8192m"

# Not compatible with Jenkins 2 yet, so comment out
# ENV JENKINS_OPTS="--handlerCountStartup=100 --handlerCountMax=300"
ENV JENKINS_OPTS="--logfile=/var/log/jenkins/jenkins.log --webroot=/var/cache/jenkins/war"
