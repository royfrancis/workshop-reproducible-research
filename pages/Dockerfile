FROM ruby:3.0.2-alpine
LABEL description = "Dockerfile for Tools for Reproducible Research site build"
MAINTAINER "Erik Fasterius" erik.fasterius@nbis.se

# RUN mkdir -p /work

WORKDIR /work

ENV BUNDLE_PATH=/work/vendor/bundle \
    BUNDLER_VERSION='2.5.17'

RUN apk update && \
    apk upgrade && \
    apk add --no-cache jq build-base curl bash && \
    gem install bundler -v $BUNDLER_VERSION

RUN rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && \
    truncate -s 0 /var/log/*log

COPY Gemfile Gemfile.lock /work/

RUN bundle install

USER root

# COPY . /work

RUN $GEM_PATH
