FROM ruby:2.6.5-alpine3.10

# 文字コード設定
ENV LANG C.UTF-8

# APP-
RUN mkdir /app
RUN mkdir /app/log
ENV APP_ROOT /app

# 共有ファイル設定
WORKDIR $APP_ROOT

ADD Gemfile $WORKDIR/Gemfile
ADD Gemfile.lock $WORKDIR/Gemfile.lock

# いろいろいんすこ
RUN set -x && \
    apk add --no-cache --update \
    libxml2-dev \
    libxslt-dev \
    libstdc++ \
    tzdata \
    nodejs \
    nodejs-npm \
    build-base \
    linux-headers \
    ca-certificates \
    postgresql-dev \
    mysql-client \
    mysql-dev \
    git \
    curl-dev
    \ && npm install -g yarn

RUN gem install bundler rails

RUN bundle install

# RUN rails webpacker:install

EXPOSE 3000
