ARG BUILD_FROM
FROM ${BUILD_FROM}

# Install dependencies
RUN apk add --no-cache \
    python3 \
    py3-pip \
    npm \
    openssl

# Install ask-cli for SMAPI access
RUN npm install -g ask-cli

# Install jellyfin-alexa-skill
RUN pip3 install --no-cache-dir --upgrade pip && \
    pip3 install --no-cache-dir jellyfin-alexa-skill

# Copy local files
COPY rootfs /

# Set permissions
RUN chmod a+x /etc/services.d/jellyfin-alexa-skill/run \
    && chmod a+x /etc/services.d/jellyfin-alexa-skill/finish

# Labels
LABEL \
    io.hass.name="Jellyfin Alexa Skill" \
    io.hass.description="Alexa skill to play media from your Jellyfin server" \
    io.hass.type="addon" \
    io.hass.version="${BUILD_VERSION}" \
    maintainer="infinityofspace <https://github.com/infinityofspace>"