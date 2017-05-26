from ubuntu:14.04

RUN apt-get update && apt-get install vim curl python-dev wget git -y
RUN curl --silent --show-error --retry 5 https://bootstrap.pypa.io/get-pip.py | sudo python2.7; \
    wget -O - https://repo.saltstack.com/apt/ubuntu/14.04/amd64/2016.11/SALTSTACK-GPG-KEY.pub | sudo apt-key add -; \
    echo 'deb http://repo.saltstack.com/apt/ubuntu/14.04/amd64/2016.11 trusty main' > /etc/apt/sources.list.d/saltstack.list && apt-get update && apt-get install salt-master -y; pip install reclass

COPY prd /srv/salt/env/prd
COPY reclass /srv/salt/reclass
COPY reclass-config.yml /etc/reclass/reclass-config.yml
COPY master.conf /etc/salt/master.d/master.conf
CMD ["/usr/bin/salt-master", "-c", "master", "--config-dir", "/etc/salt"]
