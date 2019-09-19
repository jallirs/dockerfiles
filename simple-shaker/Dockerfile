FROM docker.io/ubuntu:xenial

LABEL maintainer "Oded Le'Sage <ol7435@att.com>"

RUN set -ex ;\
    apt-get update ;\
    apt-get upgrade -y ;\
    apt-get install -y \
      wget \
      nano \
      less \
      python \
      virtualenv \
      python-dev \
      gcc \
      git \
      openssh-client \
      iproute2 \
      iperf3 \
      iputils-ping \
      bc \
      netperf \
      jq;


COPY install-shaker.sh /usr/local/bin/install-python-packages.sh;
RUN /usr/local/bin/install-python-packages.sh \
     pyshaker \
     openstackclient \
     git+https://git.openstack.org/openstack/ospurge \
     flent==1.2.2

COPY *[^install-shaker].sh spot_vm.hot /opt/

WORKDIR /opt
ENV PATH=/var/lib/shaker-venv/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
CMD ["/opt/shaker_spot.sh","/share/shaker.cfg"]
