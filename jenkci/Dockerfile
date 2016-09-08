FROM jenkins
RUN /usr/local/bin/install-plugins.sh credentials:2.1.4 docker-workflow:1.8 workflow-aggregator:2.3 github-organization-folder:1.4 credentials-binding:1.9
COPY hudson.tasks.Maven.xml /var/jenkins_home/hudson.tasks.Maven.xml
COPY demo-pipeline-config.xml /var/jenkins_home/jobs/MyPipelineDemo/config.xml
USER root
RUN apt-get update \
      && apt-get install -y sudo \
      && rm -rf /var/lib/apt/lists/*
RUN echo "jenkins ALL=NOPASSWD: ALL" >> /etc/sudoers
RUN curl -fsSL https://get.docker.com/ | sh
