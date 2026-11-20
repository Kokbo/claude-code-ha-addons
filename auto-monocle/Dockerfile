# Base image per architecture, formerly build_from in the deprecated build.yaml.
# Same images as before, so local builds are unchanged. BUILD_ARCH is passed by
# the Supervisor. TODO: move to the multi-platform
# ghcr.io/home-assistant/base-python:3.13-alpine3.22 once tested (Alpine 3.20
# base images no longer receive updates).
ARG BUILD_ARCH
ARG BUILD_FROM=ghcr.io/home-assistant/${BUILD_ARCH}-base-python:3.13-alpine3.20
FROM ${BUILD_FROM}

LABEL \
    org.opencontainers.image.title="Auto-Monocle for Home Assistant" \
    org.opencontainers.image.description="Auto-discover HA cameras and expose to Alexa via Monocle Gateway" \
    org.opencontainers.image.source="https://github.com/Kokbo/claude-code-ha-addons" \
    org.opencontainers.image.licenses="MIT"

# Install dependencies
RUN apk add --no-cache \
    bash \
    curl \
    jq \
    openjdk11-jre-headless \
    ca-certificates \
    && update-ca-certificates \
    && pip3 install --no-cache-dir requests

# Download Monocle Gateway v0.0.6
ARG BUILD_ARCH
RUN mkdir -p /opt/monocle /etc/monocle && \
    case "${BUILD_ARCH}" in \
        amd64) MONOCLE_ARCH="alpine-x64" ;; \
        aarch64) MONOCLE_ARCH="alpine-arm64" ;; \
        *) MONOCLE_ARCH="alpine-x64" ;; \
    esac && \
    curl -fsSL "https://files.monoclecam.com/monocle-gateway/linux/monocle-gateway-${MONOCLE_ARCH}-v0.0.6.tar.gz" -o /tmp/monocle.tar.gz && \
    tar -xzf /tmp/monocle.tar.gz -C /opt/monocle && \
    rm /tmp/monocle.tar.gz && \
    chmod +x /opt/monocle/monocle-gateway

# Copy scripts
COPY discover_cameras.py /opt/monocle/
COPY run.sh /opt/monocle/
RUN chmod +x /opt/monocle/run.sh

WORKDIR /opt/monocle

CMD ["/opt/monocle/run.sh"]
