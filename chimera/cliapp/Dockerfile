FROM ubuntu:xenial
RUN apt-get update && apt-get install -y \ 
  cron \
  curl \
  jq \
  && rm -rf /var/lib/apt/lists/*
WORKDIR /opt/chimera/bin
RUN curl https://devops-command-line-workshop.s3.eu-west-2.amazonaws.com/cliapp --output cliapp \
  && chmod +x cliapp
COPY ./run.sh ./run.sh
RUN chmod +x ./run.sh
# The data folder should be shared with the webapp
#ENV DATA_FOLDER=/opt/chimera/data
ENV REDIS_PORT=6379
ENV REDIS_HOST=redis
RUN mkdir /var/log/chimera \
 && touch /var/log/cron.log
ENTRYPOINT ["./run.sh"]
