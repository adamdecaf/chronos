FROM centos:7
MAINTAINER Peter Ericson <pdericson@gmail.com>

ENV CHRONOS_VERSION=2.4.0
ENV MESOS_VERSION=0.24.1

# https://github.com/Yelp/dumb-init
RUN curl -fLsS -o /usr/local/bin/dumb-init https://github.com/Yelp/dumb-init/releases/download/v1.0.2/dumb-init_1.0.2_amd64 && \
    chmod +x /usr/local/bin/dumb-init && \
    rpm -i http://repos.mesosphere.io/el/7/noarch/RPMS/mesosphere-el-repo-7-1.noarch.rpm && \
    yum -y install chronos-$CHRONOS_VERSION mesos-$MESOS_VERSION && \
    yum clean all

COPY entrypoint.sh /

ENTRYPOINT ["/usr/local/bin/dumb-init", "/entrypoint.sh"]
