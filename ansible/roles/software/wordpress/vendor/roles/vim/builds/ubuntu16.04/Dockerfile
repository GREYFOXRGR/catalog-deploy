# Dockerfile for building image that contains software stack provisioned by Ansible.
#
# USAGE:
#   $ docker build -t vim:ubuntu14.04 .
#
# Version  1.1
#

# pull base image
FROM williamyeh/ansible:ubuntu16.04-onbuild
MAINTAINER Chu-Siang Lai <chusiang.lai@gmail.com>

#
# build phase
#
# fix policy-rc.d for Docker
# @see http://www.monblocnotes.com/node/2057
# @see http://askubuntu.com/a/365912
RUN sed -i -e 's/exit\s\s*101/exit 0/' /usr/sbin/policy-rc.d

# init.
RUN apt-get install -y curl git make sudo ;\
      git clone https://github.com/chusiang/vim-and-vi-mode.ansible.role.git ;\
      cd vim-and-vi-mode.ansible.role
      
ENV PLAYBOOK vim-and-vi-mode.ansible.role/setup.yml
RUN ansible-playbook-wrapper -vvv

