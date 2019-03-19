# BareOS Web-ui Dockerfile

FROM       centos:7.6.1810
MAINTAINER Barcus <barcus@tou.nu>

env DIST=CentOS_7
env RELEASE=release/18.2/
env URL=http://download.bareos.org/bareos/$RELEASE/$DIST

RUN curl -o /etc/yum.repos.d/bareos.repo $URL/bareos.repo && \
    yum install -y bareos-webui

COPY docker-entrypoint.sh /
RUN chmod u+x /docker-entrypoint.sh
RUN tar cfvz /bareos-webui.tgz /etc/bareos-webui

EXPOSE 80

VOLUME /etc/bareos-webui

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
