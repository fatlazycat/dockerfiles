FROM alpine:3.3

ENV CONSUL_VERSION 0.7.2

RUN  apk add --update ca-certificates \
  && wget https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_linux_amd64.zip \
  && unzip consul_${CONSUL_VERSION}_linux_amd64.zip \
  && mv consul /bin/ \
  && rm -rf consul_${CONSUL_VERSION}_linux_amd64.zip \
  && cd /tmp \
  && wget -O ui.zip https://releases.hashicorp.com/consul/${CONSUL_VERSION}/consul_${CONSUL_VERSION}_web_ui.zip \
  && unzip ui.zip \
  && mkdir -p /ui \
  && mv * /ui \
  && rm -rf /tmp/* /var/cache/apk/*

# Ports
# 8300 server
# 8301 serf lan
# 8302 serf wan
# 8400 rpc
# 8500 http
# 8600 dns
#
EXPOSE 8300 8301 8301/udp 8302 8302/udp 8080

VOLUME [ "/data", "/config", "/ssl" ]

ENTRYPOINT [ "/bin/consul" ]

CMD [ "agent", "-config-dir", "/config" ]
