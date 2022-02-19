ARG RUBY_VERSION
FROM ruby:$RUBY_VERSION
ARG BUNDLER_VERSION
ENV LANG C.UTF-8

RUN apt-get update -qq && DEBIAN_FRONTEND=noninteractive apt-get install -yq --no-install-recommends xvfb ca-certificates unzip build-essential fonts-liberation vim libdbusmenu-gtk4 libgtk2.0-0 \
    && fc-cache -v \
    && apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && truncate -s 0 /var/log/*log

WORKDIR /build
RUN gem update --system &&\
    gem install -v $BUNDLER_VERSION bundler
WORKDIR /sandbox
COPY . /sandbox
RUN mkdir -p tmp/sockets
