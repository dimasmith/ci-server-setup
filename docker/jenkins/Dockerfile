FROM jenkins:2.32.3-alpine

USER root
RUN apk add --update --no-cache docker
RUN apk add --update --no-cache shadow

RUN usermod jenkins -G docker --append
RUN usermod jenkins -G ping --append

USER jenkins
