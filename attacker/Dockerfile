FROM alpine:edge

RUN apk add --update --no-cache --virtual .deps build-base \
                                                libffi-dev \
                                                py-pip \
                                                python-dev \
  && apk add --no-cache openssl-dev \
                        python \
  && pip install paramiko==2.0.8 \
  && apk del .deps

