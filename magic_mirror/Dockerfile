ARG BUILD_FROM
FROM ${BUILD_FROM}

# Add env
ENV LANG C.UTF-8

# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_DESCRIPTION
ARG BUILD_NAME
ARG BUILD_REF
ARG BUILD_REPOSITORY
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="${BUILD_NAME}" \
    io.hass.description="${BUILD_DESCRIPTION}" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="@SirUli" \
    org.opencontainers.image.title="${BUILD_NAME}" \
    org.opencontainers.image.description="${BUILD_DESCRIPTION}" \
    org.opencontainers.image.vendor="wolf-u.li" \
    org.opencontainers.image.authors="@SirUli" \
    org.opencontainers.image.source="https://github.com/${BUILD_REPOSITORY}" \
    org.opencontainers.image.documentation="https://github.com/${BUILD_REPOSITORY}/blob/main/README.md" \
    org.opencontainers.image.created=${BUILD_DATE} \
    org.opencontainers.image.revision=${BUILD_REF} \
    org.opencontainers.image.version=${BUILD_VERSION}

# Setup base
RUN apk add --no-cache \
  git \
  nodejs \
  npm \
  curl \
  wget \
  unzip \
    && npm i npm@latest -g 

# Copy root filesystem
COPY rootfs /

WORKDIR /opt/magic_mirror

# Copy data
RUN chmod a+x /run.sh /etc/services.d/magic_mirror/*
