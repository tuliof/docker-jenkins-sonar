FROM jenkins:2.60.1-alpine
COPY plugins.txt /usr/share/jenkins/plugins.txt
RUN /usr/local/bin/plugins.sh /usr/share/jenkins/plugins.txt
# Set the user as root, otherwise it won't be able to write to the volumes
# There is another way of fixing this issue.
USER root