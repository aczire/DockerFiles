# CDH5 
FROM aczire/centos7-jdk7
MAINTAINER Jimson K James "mail.jimson@aczire.com"
ENV REFRESHED_AT 2014-12-01

RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/libedit-3.0-12.20121213cvs.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/openssh-6.4p1-8.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/openssh-server-6.4p1-8.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/openssh-clients-6.4p1-8.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/openssh-server-sysvinit-6.4p1-8.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/tar-1.26-29.el7.x86_64.rpm
#RUN rpm -Uvh http://mirror.centos.org/centos/7/os/x86_64/Packages/passwd-0.79-4.el7.x86_64.rpm

RUN yum install -y openssh openssh-server openssh-clients
RUN yum install initscripts

RUN ssh-keygen -t rsa -q -N "" < /dev/zero > /dev/null 2>&1

# Passwordless SSH to localhost
RUN cat ~/.ssh/id_rsa.pub > ~/.ssh/authorized_keys
RUN ssh-keyscan localhost > ~/.ssh/known_hosts

RUN mkdir -p /var/run/sshd
RUN chmod -rx /var/run/sshd
RUN ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -q -N "" < /dev/zero > /dev/null 2>&1
RUN sed -ri 's/#PermitRootLogin yes/PermitRootLogin yes/g' /etc/ssh/sshd_config
RUN service sshd restart