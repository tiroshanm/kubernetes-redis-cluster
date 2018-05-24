# Alpine with ruby support image
FROM redis:latest

ENV DEBIAN_FRONTEND noninteractive
RUN apt-get -y update \
  && apt-get -y upgrade \
  && apt-get -y --no-install-recommends install ruby  wget \
  && gem install redis -v 3.3.5 \
  && apt-get -y autoremove \
  && apt-get -y clean

# Copy redis-trib.rb
RUN wget -O /usr/local/bin/redis-trib http://download.redis.io/redis-stable/src/redis-trib.rb
RUN chmod 755 /usr/local/bin/redis-trib

# Copy redis.conf, port=7000, datadir=/data/
RUN mkdir -p /redis-conf
COPY redis.conf /redis-conf/redis.conf


# Install ruby and ruby-bundler
RUN apt-get install -y rubygems
