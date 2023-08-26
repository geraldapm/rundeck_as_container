FROM redhat/ubi8:latest
MAINTAINER Gerald Mahayadnya

RUN yum -y update \
  && yum install -y ca-certificates python3 wget\
    python3-pip python3-setuptools git sshpass zip unzip rpm-build \
  && yum clean all

COPY ./ansible.cfg /etc/ansible/ansible.cfg

RUN pip3 --no-cache-dir install --upgrade pip \
  && pip3 --no-cache-dir install ansible ansible-lint