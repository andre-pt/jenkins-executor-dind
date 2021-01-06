FROM jenkins/slave:latest

ARG COMPOSE_VERSION=1.27.4

USER root

RUN curl -sSL https://get.docker.com/ | sh && \
    curl -L https://github.com/docker/compose/releases/download/${COMPOSE_VERSION}/docker-compose-Linux-x86_64 > /usr/local/bin/docker-compose && \
    chmod +x /usr/local/bin/docker-compose && \
    apt-get autoremove -yqq && \
    apt-get autoclean -yqq && \
    rm -rf \
        /tmp/* \
        /var/cache/apt/archives/* \
        /var/lib/apt/lists/* \
        /var/tmp/*

USER ${user}