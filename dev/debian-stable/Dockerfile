FROM debian:stable
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /
RUN chmod +x debian-setup.sh \
	&& apt-get update \
	&& ./debian-setup.sh --install-optional --install-test-deps -y --install-deb-deps
