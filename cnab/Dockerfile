FROM python:3-alpine

RUN apk update
RUN apk add -u bash git

ARG AWSCLI_VERSION=1.16.77
RUN pip install awscli==${AWSCLI_VERSION}

ARG HUGO_VERSION=0.52
RUN wget https://github.com/gohugoio/hugo/releases/download/v${HUGO_VERSION}/hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && tar -zxvf hugo_${HUGO_VERSION}_Linux-64bit.tar.gz && mv hugo /usr/bin/

COPY app /cnab/app

CMD ["/cnab/app/run"]
