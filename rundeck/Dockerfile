
FROM rundeck/rundeck:4.8.0
MAINTAINER Gerald Mahayadnya

USER rundeck

RUN sudo apt-get -y update \
  && sudo apt-get upgrade -y --no-install-recommends\
  && sudo apt-get -y --no-install-recommends install ca-certificates python3\
    python3-pip python3-setuptools git\
    python3-venv sshpass zip unzip ssh\
    ansible ansible-lint\
  && sudo rm -rf /var/lib/apt/lists/*

COPY ./ansible.cfg /etc/ansible/ansible.cfg


ENTRYPOINT [ "/tini", "--", "docker-lib/entry.sh" ]
