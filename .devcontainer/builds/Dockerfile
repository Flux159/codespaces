FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:16

USER root

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends curl wget jq ripgrep postgresql-common vim python3-pip python3-setuptools
RUN npm install --global yarn
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" | tee  /etc/apt/sources.list.d/pgdg.list
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive && apt-get -y install --no-install-recommends postgresql-12
RUN echo "node\nnode\n" | passwd node 
RUN pip3 install notebook requests

USER node

RUN echo "PATH=\$PATH:/usr/lib/postgresql/12/bin" >> /home/node/.bashrc
