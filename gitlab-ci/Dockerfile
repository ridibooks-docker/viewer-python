FROM docker:latest

ARG CHAMBER_VERSION=2.3.2

RUN apk update
RUN apk add python3 \
    make \
    mariadb-dev \
    python3-dev \
    libffi-dev \
    musl-dev \
    gcc \
    curl
RUN rm -rf /var/cache/apk/*

# install chamber
RUN curl -Lo /usr/local/bin/chamber https://github.com/segmentio/chamber/releases/download/v${CHAMBER_VERSION}/chamber-v${CHAMBER_VERSION}-linux-amd64 \
    && chmod +x /usr/local/bin/chamber 

# install ecl-cli
RUN curl -o /usr/local/bin/ecs-cli https://s3.amazonaws.com/amazon-ecs-cli/ecs-cli-linux-amd64-latest
RUN chmod +x /usr/local/bin/ecs-cli

RUN pip3 install --upgrade pip

ADD requirements.txt /tmp/requirements.txt
RUN pip3 install -r /tmp/requirements.txt
