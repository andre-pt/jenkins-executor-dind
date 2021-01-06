FROM andrepm/jenkins-executor-dind:latest

ARG MAVEN_VERSION=3.6.3

USER root

RUN curl --create-dirs -fsSLo /tmp/maven.tar.gz https://mirror.klaus-uwe.me/apache/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz \
    && mkdir -p /opt/maven \
    && tar -xzvf /tmp/maven.tar.gz --strip 1 -C /opt/maven \
    && rm /tmp/maven.tar.gz

ENV PATH="/opt/maven/bin:$PATH"

USER ${user}