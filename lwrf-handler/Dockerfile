ARG BUILD_FROM=hassioaddons/base:2.2.0
# hadolint ignore=DL3006
FROM ${BUILD_FROM}

# Copy root filesystem
#COPY rootfs /

# Setup base
RUN \
    apk add --no-cache \
        git=2.18.0-r0 \
        nodejs=8.11.4-r0 \
        npm=8.11.4-r0 \
    && git clone \
        git://github.com/adamclark-dev/smartthings-lightwave-node-server.git /app/lwrf
# Script to run after startup
COPY run.sh /
RUN chmod a+x /run.sh

CMD [ "/run.sh" ]

# Build arugments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="lwrf_handler" \
    io.hass.description="LightWaveRF Handler for hassio" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Jamie Murphy - ITJamie" \
    org.label-schema.description="LightWaveRF Handler for hassio" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="LWRF-Handler" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://addons.community" \
    org.label-schema.usage="https://github.com/hassio-addons/addon-example/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/hassio-addons/addon-example" \
    org.label-schema.vendor="ITJamie"
