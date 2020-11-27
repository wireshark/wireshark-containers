FROM debian:stable
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /debian-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/debian-setup.sh /debian-setup-3.4.sh
RUN chmod -v +x debian-setup*.sh \
	&& apt-get update \
	&& ./debian-setup-3.4.sh --install-optional --install-test-deps -y --install-deb-deps \
	&& ./debian-setup-master.sh --install-optional --install-test-deps -y --install-deb-deps
