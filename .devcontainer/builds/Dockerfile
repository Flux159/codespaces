FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:16

# NOTE: This should probably be setup in docker registry as a prebuilt image & just keep this as a reference
# Would save like a minute in starting up (along w/ improvements with yarn offline mirror saves like 2 mins off startup time)

# ** [Optional] Uncomment this section to install additional packages. **
USER root

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends curl wget jq ripgrep postgresql-common vim python3-pip
# RUN curl -sL https://deb.nodesource.com/setup_16.x | bash && apt-get install -y nodejs
RUN npm install --global yarn
RUN wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add -
RUN echo "deb http://apt.postgresql.org/pub/repos/apt/ `lsb_release -cs`-pgdg main" | tee  /etc/apt/sources.list.d/pgdg.list
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive && apt-get -y install --no-install-recommends postgresql-12
RUN echo "node\nnode\n" | passwd node 
RUN pip3 install notebook requests

USER node

RUN echo "PATH=\$PATH:/usr/lib/postgresql/12/bin" >> /home/node/.bashrc
# RUN echo "source /usr/local/share/nvm/nvm.sh && nvm install v16.5.0" >> /home/node/.bashrc
