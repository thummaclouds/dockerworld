# Ubunutu 14.04 Base

FROM ubuntu:14.04 

MAINTAINER thummaclouds <thumma@gmail.com>

RUN apt-get update && apt-get install -y supervisor wget  

VOLUME ["/logs"]

ADD config/supervisord.conf /etc/supervisor/supervisord.conf
ADD config/supervisor-http.ini /etc/supervisor/conf.d/supervisor-http.ini
ADD config/supervisord.sh /etc/supervisor/supervisord.sh
ADD config/supervisorctl.sh /etc/supervisor/supervisorctl.sh

RUN chmod +x /etc/supervisor/supervisord.sh
RUN chmod +x /etc/supervisor/supervisorctl.sh

 
ADD config/bootstrap.sh /etc/supervisor/bootstrap.sh
RUN chmod +x /etc/supervisor/bootstrap.sh

# PORT for supervisord HTTP interface
EXPOSE 9001

ENTRYPOINT  ["/etc/supervisor/bootstrap.sh"]
CMD ["/usr/bin/supervisord","-n","-c","/etc/supervisor/supervisord.conf"]


