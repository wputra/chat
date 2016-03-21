FROM qiscus/base

RUN apt-get install -y software-properties-common && apt-add-repository ppa:brightbox/ruby-ng

RUN apt-get update && apt-get install -y ruby2.1 ruby2.1-dev build-essential

RUN apt-get install -y zlib1g-dev libmysqlclient-dev graphviz

RUN apt-get install -y curl libcurl3 libcurl3-gnutls libcurl4-openssl-dev libpq5 libpq-dev sqlite3 libsqlite3-dev

RUN apt-get install -y imagemagick libmagickcore5 libmagickcore-dev libmagickwand5 libmagickwand-dev

RUN gem install bundler

RUN mkdir /qiscus

WORKDIR /qiscus

ADD Gemfile /qiscus/Gemfile

ENV BUNDLE_GEMFILE=/qiscus/Gemfile BUNDLE_JOBS=2 BUNDLE_PATH=/bundle

RUN bundle install
