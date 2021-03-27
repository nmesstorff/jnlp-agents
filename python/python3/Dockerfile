FROM jenkins/inbound-agent:alpine as jnlp

FROM python:alpine

RUN apk -U add openjdk8-jre

COPY --from=jnlp /usr/local/bin/jenkins-agent /usr/local/bin/jenkins-agent
COPY --from=jnlp /usr/share/jenkins/agent.jar /usr/share/jenkins/agent.jar

RUN apk update && apk upgrade && apk add --no-cache git openssh-client zlib-dev jpeg-dev build-base imagemagick-dev optipng npm && \
     pip install --upgrade pip && \
     npm -g install svgo

ENTRYPOINT ["/usr/local/bin/jenkins-agent"]
