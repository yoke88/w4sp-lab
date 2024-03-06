#get the base default ubuntu 14.04 image
FROM ubuntu:18.04

MAINTAINER w4sp-book

#adding a label here so we can easily delete our containers
LABEL w4sp=true


ENV DEBIAN_FRONTEND noninteractive
# fix non apt https and control charators error
RUN sed -i -e 's/http:/https:/g' -e 's/security.ubuntu.com/mirrors.ustc.edu.cn/g' -e 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list 
RUN apt -o "Acquire::https::Verify-Peer=false" update -y &&apt-get -o "Acquire::https::Verify-Peer=false" install ca-certificates -y

RUN apt-get -y install wireshark tshark 
RUN apt-get -y install bridge-utils ethtool
RUN apt-get -y install nmap mtr traceroute python wget curl supervisor 
RUN apt-get -y install python-pip python-dev smbclient
RUN apt-get -y install iptables

# fix update-locale can not found
RUN apt-get -y install locales 

#set root creds to w4sp:w4spbook and create w4sp user with same password
RUN usermod -p '$6$teB23uhk$u00/htDYpQKbBCVC2GsbcEi1m1BplEOnCs0LDE7cFM5lgq/VMSU27g7IFGRWp8k2qCd0jyiEFm5jx4.1LBrXZ.' root
RUN useradd -d /home/w4sp -m -p '$6$teB23uhk$u00/htDYpQKbBCVC2GsbcEi1m1BplEOnCs0LDE7cFM5lgq/VMSU27g7IFGRWp8k2qCd0jyiEFm5jx4.1LBrXZ.' -s /bin/bash w4sp

#fix unnecessary errors down the line
RUN update-locale

#install python dependencies
RUN pip install netifaces

#create directory for child images to store configuration in
RUN  mkdir -p /var/log/supervisor && mkdir -p /etc/supervisor/conf.d

#supervisor base configuration
ADD supervisor.conf /etc/supervisor.conf
#add conf for dhclient
ADD supervisor_dhclient.conf /etc/supervisor/conf.d/supervisor_dhclient.conf

# default command
CMD ["supervisord", "-c", "/etc/supervisor.conf"]


