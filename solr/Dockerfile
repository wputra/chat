FROM qiscus/base

RUN sed -i 's/archive/ap-southeast-1.ec2.archive/g' /etc/apt/sources.list \
	&& echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" >> /etc/apt/sources.list.d/webupd8team-java.list \
	&& apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys EEA14886 \
	&& apt-get update \
	&& echo debconf shared/accepted-oracle-license-v1-1 select true | debconf-set-selections \
	&& apt-get install -y oracle-java8-installer \
	&& apt-get autoremove -y \
	&& apt-get clean \
	&& rm -rf /var/cache/apt /var/lib/apt/lists/* /var/tmp/* /tmp/* \
	&& useradd jetty -M -U -s /bin/false

ADD jetty.sh /
WORKDIR /opt

EXPOSE 8080
CMD ["/jetty.sh", "start"]
