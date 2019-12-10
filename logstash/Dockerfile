# Wazuh App Copyright (C) 2019 Wazuh Inc. (License GPLv2)
FROM docker.elastic.co/logstash/logstash:7.4.2

USER root

RUN yum install -y git

USER 1000

COPY --chown=logstash:logstash config/entrypoint.sh /entrypoint.sh

RUN chmod 755 /entrypoint.sh

RUN rm -f /usr/share/logstash/pipeline/logstash.conf

#RUN /usr/share/logstash/bin/logstash-plugin install logstash−input−blueliv

COPY config/01-wazuh.conf /usr/share/logstash/pipeline/01-wazuh.conf

COPY config/logstash-input-blueliv-1.1.0.gem /usr/share/logstash/pipeline/logstash-input-blueliv-1.1.0.gem

ENTRYPOINT /entrypoint.sh
