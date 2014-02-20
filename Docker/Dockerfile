FROM centos

MAINTAINER Rodney Cobb <roacobb@gmail.com>

RUN yum -y update

RUN yum -y install http://ftp.riken.jp/Linux/fedora/epel/6/i386/epel-release-6-8.noarch.rpm

RUN yum -y install python-setuptools

RUN easy_install supervisor

RUN mkdir -p /var/log/supervisor

RUN yum -y install which

RUN yum -y install git

RUN yum -y install httpd

ADD supervisord.conf /etc/supervisord.conf

EXPOSE 22 80

CMD ["/usr/bin/supervisord"]
