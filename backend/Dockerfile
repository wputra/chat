FROM qiscus/base

ENV BUNDLE_GEMFILE=/qiscus/Gemfile BUNDLE_JOBS=2 BUNDLE_PATH=/bundle
RUN echo 'deb http://ppa.launchpad.net/brightbox/ruby-ng/ubuntu trusty main' >> /etc/apt/sources.list.d/brightbox-ruby-ng-trusty.list && \
	sed -i 's/archive/ap-southeast-1.ec2.archive/g' /etc/apt/sources.list && \
	apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys F5DA5F09C3173AA6 && \
	apt-get update && apt-get install -y \
	ruby2.1 \
	ruby2.1-dev \
	build-essential \
	openssl \
	ca-certificates \
	curl \
	libcurl3 \
	libcurl3-gnutls \
	libcurl4-openssl-dev \
	libpq5 \
	libpq-dev \
	git-core \
	imagemagick \
	libmagickcore5 \
	libmagickcore-dev \
	libmagickwand5 \
	libmagickwand-dev && \
	apt-get autoremove -y && \
	apt-get clean && \
	rm -rf /var/cache/apt /var/lib/apt/lists/* /var/tmp/* /tmp/*

ADD build.sh
RUN bash build.sh

WORKDIR /qiscus
CMD ["bundle", "exec", "puma", "-C", "config/puma.rb"]