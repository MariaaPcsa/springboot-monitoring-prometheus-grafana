FROM debian

USER root

COPY ./client.sh /scripts/client.sh

RUN apt update && \
    apt install -y curl && \
    rm -rf /var/lib/apt/lists/* && \
    chmod +x /scripts/client.sh

ENTRYPOINT ["/scripts/client.sh"]
