# OmniRoute — The Free AI Gateway
# This Dockerfile is designed for a Home Assistant Add-on.
# It uses the existing OmniRoute image to ensure stability and ease of use.

ARG OMNIROUTE_VERSION=3.8.46
FROM diegosouzapw/omniroute:v${OMNIROUTE_VERSION}

# Home Assistant add-ons usually run as root or a specific user.
# The OmniRoute image uses 'node'. We'll ensure the directory exists.
# We can also add any additional system dependencies if needed.

# Setting environment variables for HA Add-on compatibility
ENV PORT=20128
ENV HOSTNAME=0.0.0.0
ENV OMNIROUTE_MEMORY_MB=1024
ENV DATA_DIR=/data

# Ensure the data directory is writable by the node user
RUN mkdir -p /data && chown -R node:node /data

# We'll use the same entrypoint as the original image
# but we might need to adjust it if HA requires a specific signal handling.
# For now, we stick to the original.
ENTRYPOINT ["/tmp/check-permissions.sh"]
CMD ["node", "dev/run-standalone.mjs"]
