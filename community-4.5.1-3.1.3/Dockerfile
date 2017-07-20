FROM couchbase:community-4.5.1

ENV CONTAINERPILOT_VERSION=3.1.3
ENV CONTAINERPILOT_SOURCE=https://github.com/joyent/containerpilot/releases/download/$CONTAINERPILOT_VERSION/containerpilot-$CONTAINERPILOT_VERSION.tar.gz
ENV CONTAINERPILOT=/etc/containerpilot.json

# get ContainerPilot release
RUN curl -Lo /tmp/cb.tar.gz $CONTAINERPILOT_SOURCE && \
      tar -xz -f /tmp/cb.tar.gz && \
      mv containerpilot /bin/

COPY containerpilot.json $CONTAINERPILOT

# 8091: Couchbase Web console, REST/HTTP interface
# 8092: Views, queries, XDCR
# 8093: Query services (4.0+)
# 8094: Full-text Search (4.5+)
# 11207: Smart client library data node access (SSL)
# 11210: Smart client library/moxi data node access
# 11211: Legacy non-smart client library data node access
# 18091: Couchbase Web console, REST/HTTP interface (SSL)
# 18092: Views, query, XDCR (SSL)
# 18093: Query services (SSL) (4.0+)
EXPOSE 8091 8092 8093 8094 11207 11210 11211 18091 18092 18093

VOLUME /opt/couchbase/var

CMD ["containerpilot"]
