FROM openliberty/open-liberty:full-java17-openj9-ubi

ARG VERSION=1.0
ARG REVISION=SNAPSHOT

LABEL \
  vendor="PD Professional" \
  name="spring-boot" \
  version="$VERSION-$REVISION" \
  summary="Liberty Spring Boot Sample Docker Image" \
  description="This image contains the spring-boot running with the Open Liberty runtime."

USER root
# make is for snapit
# porcps-ng is for vmstat, ps, top (in linperf.sh)
# net-tools is for netstat (in inperf.sh)
# gdb is for gcore
RUN dnf install -y make procps-ng net-tools gdb
COPY --chown=1001:0 config/server.xml /config/
COPY --chown=1001:0 config/jvm.options /config/
COPY --chown=1001:0 apps/pdprof-0.0.1-SNAPSHOT.war /config/apps/

USER 1001
