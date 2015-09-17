FROM ubuntu:14.04

MAINTAINER Jason Hane <jasonhane@gmail.com>

ENV DEBIAN_FRONTEND noninteractive

RUN echo "deb http://ppa.launchpad.net/mythbuntu/0.27/ubuntu trusty main" >> /etc/apt/sources.list && \
    apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 1504888C && \
    apt-get update && \
    apt-get -y upgrade && \
    apt-get -y install mythtv-backend && \
    apt-get clean

# Set the timezone and locale
RUN echo "America/New_York" > /etc/timezone && \
    dpkg-reconfigure -f noninteractive tzdata && \
    update-locale LANG=C.UTF-8 LC_MESSAGES=POSIX && \
    locale-gen en_US.UTF-8 && \
    dpkg-reconfigure locales

COPY assets/config.xml /etc/mythtv/config.xml

EXPOSE 6543 6544

VOLUME ["/data"]

CMD ["mythbackend", "-v"]

