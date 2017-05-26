from ubuntu:14.04

RUN apt-get update && apt-get install vim curl python-dev wget -y
RUN curl --silent --show-error --retry 5 https://bootstrap.pypa.io/get-pip.py | sudo python2.7; \
    wget -O - https://repo.saltstack.com/apt/ubuntu/14.04/amd64/2016.11/SALTSTACK-GPG-KEY.pub | sudo apt-key add -; \
    echo 'deb http://repo.saltstack.com/apt/ubuntu/14.04/amd64/2016.11 trusty main' > /etc/apt/sources.list.d/saltstack.list && apt-get update && apt-get install salt-minion -y

COPY minion.conf /etc/salt/minion.d/minion.conf
CMD ["/usr/bin/salt-minion", "-c", "minion", "--config-dir", "/etc/salt"]
