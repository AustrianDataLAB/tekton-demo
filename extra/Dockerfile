# Helm Rootless docker image.
# docker build -t mbwali/helm-rootless:latest .
# docker push mbwali/helm-rootless:latest

FROM alpine

LABEL maintainer="Mojib Wali"

# Create a group and user
RUN addgroup -g 1000 helm && \
    adduser -u 1000 -G helm -h /home/helm -D helm

# Metadata
LABEL org.opencontainers.image.title="mbwali/helm-rootless" \
      org.opencontainers.image.url="https://helm.sh/docs/"

ENV HELM_LATEST_VERSION="v3.10.2"

ARG TARGETARCH
ENV TARGETARCH=${TARGETARCH:-amd64}

RUN apk add --update ca-certificates \
 && apk add --update -t deps wget git openssl bash \
 && wget -q https://get.helm.sh/helm-${HELM_LATEST_VERSION}-linux-${TARGETARCH}.tar.gz \
 && tar -xf helm-${HELM_LATEST_VERSION}-linux-${TARGETARCH}.tar.gz \
 && mv linux-${TARGETARCH}/helm /usr/local/bin \
 && apk del --purge deps \
 && rm /var/cache/apk/* \
 && rm -f /helm-${HELM_LATEST_VERSION}-linux-${TARGETARCH}.tar.gz

USER helm


ENTRYPOINT ["helm"]
CMD ["help"]
