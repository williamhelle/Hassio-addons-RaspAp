ARG BUILD_FROM
# hadolint ignore=DL3006
FROM ${BUILD_FROM}


# Set shell
SHELL ["/bin/bash", "-o", "pipefail", "-c"]

RUN apt-get update
RUN apt-get install -y software-properties-common 
RUN add-apt-repository ppa:ondrej/php
RUN apt-get install -y git iptables iproute2 iw wpasupplicant net-tools
RUN apt-get install -y hostapd qrencode dnsmasq lighttpd vnstat
RUN apt-get install -y dhcpcd5
RUN apt-get install -y php7.3-cgi
RUN apt-get install -y node.js
RUN apt-get install -y git

# RUN rm -Rf /var/www/html
# RUN git clone --branch 2.8.4 https://github.com/RaspAP/raspap-webgui /var/www/html 
 
COPY /rootfs / 
# TODO wpa_supplicant -Dnl80211 -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf

RUN cp /var/www/html/config/50-raspap-router.conf /etc/lighttpd/conf-available
RUN ln -s /etc/lighttpd/conf-available/50-raspap-router.conf /etc/lighttpd/conf-enabled/50-raspap-router.conf


# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="chatcord_v2" \
    io.hass.description="chatcord_v2" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Williamhelle <williamhelle@icloud.com>" \
    org.label-schema.description="chatcord_v2" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="hotspot_wifi" \
    org.label-schema.schema-version="1.0" \
    org.label-schema.url="https://github.com/williamhelle/Hassio-addons-RaspAp" \
    org.label-schema.usage="https://github.com/williamhelle/Hassio-addons-RaspAp/blob/master/chatcordv2/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/williamhelle/Hassio-addons-RaspAp/tree/master/chatcordv2" \
    org.label-schema.vendor="Williamhelle"
