FROM prom/prometheus:v2.2.0-rc.0
COPY prometheus.yml /etc/prometheus/prometheus.yml
COPY target_up.yml /etc/prometheus/target_up.yml
COPY site_up.yml /etc/prometheus/site_up.yml
COPY cpu.yml /etc/prometheus/cpu.yml
COPY localtime /etc/localtime
WORKDIR /
USER root
ADD curl-7.30.0.ermine.tar.bz2 .
RUN mv /curl-7.30.0.ermine/curl.ermine /bin/curl     && rm -Rf /curl-7.30.0.ermine
HEALTHCHECK --interval=10s --timeout=10s --retries=3 CMD curl -f http://127.0.0.1:9090/ || exit 1
