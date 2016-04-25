FROM alpine:3.3

ENV VAULT_VERSION 0.5.2

RUN  apk add --update ca-certificates \
  && wget https://releases.hashicorp.com/vault/${VAULT_VERSION}/vault_${VAULT_VERSION}_linux_amd64.zip \
  && unzip vault_${VAULT_VERSION}_linux_amd64.zip \
  && mv vault /bin/ \
  && rm -rf vault_${VAULT_VERSION}_linux_amd64.zip \
  && rm -rf /var/cache/apk/*

# Ports
# Listener Port
#
EXPOSE 8200

VOLUME [ "/config", "/ssl" ]

ENTRYPOINT [ "/bin/vault" ]

CMD [ "server", "-config", "/config" ]
