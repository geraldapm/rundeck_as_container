
FROM rundeck/rundeck:4.8.0
MAINTAINER Gerald Mahayadnya

# install ansible
# base image already installed: curl, openjdk-8-jdk-headless, ssh-client, sudo, uuid-runtime, wget
# (see https://github.com/rundeck/rundeck/blob/master/docker/ubuntu-base/Dockerfile)

USER rundeck

RUN sudo apt-get -y update \
  && sudo apt-get upgrade -y --no-install-recommends\
  && sudo apt-get -y --no-install-recommends install ca-certificates python3\
    python3-pip python3-setuptools git\
    python3-venv sshpass zip unzip ssh\
  # https://pypi.org/project/ansible/#history
  && sudo rm -rf /var/lib/apt/lists/* \
  && sudo mkdir /etc/ansible

COPY ./ansible.cfg /etc/ansible/ansible.cfg
RUN sudo -H pip3 install --upgrade pip \
  && sudo -H pip3 --no-cache-dir install ansible ansible-lint

# ENTRYPOINT ["sudo ssh-keygen"]
# ENTRYPOINT ["sudo /etc/init.d/ssh", "restart"]

ENTRYPOINT [ "/tini", "--", "docker-lib/entry.sh" ]
