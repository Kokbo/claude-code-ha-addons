# Build directly on the official Playwright image (Ubuntu Noble).
# It ships Chromium in /ms-playwright/ (required by run.sh) and has apt-get.
# Hardcoded on purpose: without a build.yaml the Supervisor passes no BUILD_FROM.
# The io.hass.* labels (version, arch, type) are set by the Supervisor at build time.
FROM mcr.microsoft.com/playwright:v1.57.0-noble

LABEL \
    org.opencontainers.image.title="Playwright Browser for Home Assistant" \
    org.opencontainers.image.description="Headless Chromium with CDP endpoint for browser automation" \
    org.opencontainers.image.source="https://github.com/Kokbo/claude-code-ha-addons" \
    org.opencontainers.image.licenses="MIT"

# jq is already available in the Playwright image (Ubuntu-based)
# Just ensure it's installed
RUN apt-get update && \
    apt-get install -y --no-install-recommends jq curl nginx && \
    rm -rf /var/lib/apt/lists/*

# Create data directory
RUN mkdir -p /data

# Copy run script
COPY run.sh /run.sh
RUN chmod +x /run.sh

# Expose CDP port
EXPOSE 9222

# Health check - verify CDP endpoint responds
HEALTHCHECK --interval=30s --timeout=10s --start-period=10s --retries=3 \
    CMD curl -sf http://localhost:9222/json/version || exit 1

CMD ["/run.sh"]
