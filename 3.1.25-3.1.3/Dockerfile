FROM arangodb/arangodb:3.1.25

ENV CONTAINERPILOT_VERSION=3.1.3
ENV CONTAINERPILOT_SOURCE=https://github.com/joyent/containerpilot/releases/download/$CONTAINERPILOT_VERSION/containerpilot-$CONTAINERPILOT_VERSION.tar.gz
ENV CONTAINERPILOT=/etc/containerpilot.json

# get ContainerPilot release
RUN curl -Lo /tmp/cb.tar.gz $CONTAINERPILOT_SOURCE && \
      tar -xz -f /tmp/cb.tar.gz && \
      mv containerpilot /bin/

COPY containerpilot.json $CONTAINERPILOT

# Pulled from the parent image
ENTRYPOINT ["/entrypoint.sh"]

EXPOSE 8529 8529
CMD ["containerpilot"]
