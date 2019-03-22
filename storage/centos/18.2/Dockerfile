# Dockerfile BareOS storage daemon

FROM       centos:7.6.1810
MAINTAINER Barcus <barcus@tou.nu>

env DIST=CentOS_7
env RELEASE=release/18.2/
env URL=http://download.bareos.org/bareos/$RELEASE/$DIST

RUN curl -o /etc/yum.repos.d/bareos.repo $URL/bareos.repo && \
    yum install -y bareos-storage bareos-tools bareos-storage-droplet libdroplet

COPY docker-entrypoint.sh /
RUN chmod u+x /docker-entrypoint.sh
RUN tar cfvz /bareos-sd.tgz /etc/bareos/bareos-sd.d

EXPOSE 9103

VOLUME /etc/bareos
VOLUME /var/lib/bareos/storage

ENTRYPOINT ["/docker-entrypoint.sh"]
CMD ["/usr/sbin/bareos-sd", "-u", "bareos", "-f"]
