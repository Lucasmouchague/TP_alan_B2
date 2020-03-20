FROM ubuntu
MAINTAINER tamere
RUN apt update && apt upgrade -y \
    && apt install apache2 libapache2-mod-security2 git -y 
RUN cp /etc/modsecurity/modsecurity.conf-recommended  /etc/modsecurity/modsecurity.conf \
    && git clone https://github.com/SpiderLabs/owasp-modsecurity-crs.git \
    && cd owasp-modsecurity-crs \
    && ls /etc/modsecurity/ \
    && rm /etc/modsecurity/crs/crs-setup.conf \
    && mv crs-setup.conf.example /etc/modsecurity/crs/crs-setup.conf \
    && mv rules/ /etc/modsecurity/ 
EXPOSE 80 443

COPY ./modsecurity_conf/security2.conf /etc/apache2/mods-available/security2.conf

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]

