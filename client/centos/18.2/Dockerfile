# Dockerfile BareOS client/file daemon

FROM       centos:7.6.1810
MAINTAINER Barcus <barcus@tou.nu>

env DIST=CentOS_7
env RELEASE=release/18.2/
env URL=http://download.bareos.org/bareos/$RELEASE/$DIST

RUN curl -o /etc/yum.repos.d/bareos.repo $URL/bareos.repo && \
      yum install -y bareos-client mysql-client postgresql-client bareos-tools

COPY docker-entrypoint.sh /
RUN chmod u+x /docker-entrypoint.sh
RUN tar cfvz /bareos-fd.tgz /etc/bareos/bareos-fd.d

EXPOSE 9102

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/usr/sbin/bareos-fd", "-u", "bareos", "-f"]
