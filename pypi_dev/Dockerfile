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
RUN apt-get install -y python3-pip
RUN apt install build-essential python3-dev python3-pip -y
RUN apt install -y \
        python3-gst-1.0 \
        gir1.2-gstreamer-1.0 \
        gir1.2-gst-plugins-base-1.0 \
        gstreamer1.0-plugins-good \
        gstreamer1.0-plugins-ugly \
        gstreamer1.0-tools

# RUN rm -Rf /var/www/html
# RUN git clone --branch 2.8.4 https://github.com/RaspAP/raspap-webgui /var/www/html 
 
COPY /rootfs / 
# TODO wpa_supplicant -Dnl80211 -i wlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf

# RUN cp /var/www/html/config/50-raspap-router.conf /etc/lighttpd/conf-available
# RUN ln -s /etc/lighttpd/conf-available/50-raspap-router.conf /etc/lighttpd/conf-enabled/50-raspap-router.conf


# Build arguments
ARG BUILD_ARCH
ARG BUILD_DATE
ARG BUILD_REF
ARG BUILD_VERSION

# Labels
LABEL \
    io.hass.name="pypi" \
    io.hass.description="pypi" \
    io.hass.arch="${BUILD_ARCH}" \
    io.hass.type="addon" \
    io.hass.version=${BUILD_VERSION} \
    maintainer="Williamhelle <williamhelle@icloud.com>" \
    org.label-schema.description="pypi" \
    org.label-schema.build-date=${BUILD_DATE} \
    org.label-schema.name="pypi" \
    org.label-schema.schema-version="1.0.0" \
    org.label-schema.url="https://github.com/williamhelle/Hassio-addons-RaspAp" \
    org.label-schema.usage="https://github.com/williamhelle/Hassio-addons-RaspAp/tree/master/pypi_dev/tree/master/README.md" \
    org.label-schema.vcs-ref=${BUILD_REF} \
    org.label-schema.vcs-url="https://github.com/williamhelle/Hassio-addons-RaspAp/tree/master/pypi_dev" \
    org.label-schema.vendor="Williamhelle"
