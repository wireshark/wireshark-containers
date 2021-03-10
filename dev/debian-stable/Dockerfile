FROM debian:stable
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /debian-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/debian-setup.sh /debian-setup-3.4.sh
ENV COMMON_APT_GET_ARGS="--yes --no-install-recommends"
RUN export DEBIAN_FRONTEND="noninteractive" DEBCONF_NONINTERACTIVE_SEEN=true \
	&& printf "tzdata tzdata/Areas select Etc\ntzdata tzdata/Zones/Etc select UTC" | debconf-set-selections \
	&& chmod -v +x debian-setup*.sh \
	&& apt-get update \
	&& ./debian-setup-3.4.sh ${COMMON_APT_GET_ARGS} --install-optional --install-test-deps --install-deb-deps \
	&& ./debian-setup-master.sh ${COMMON_APT_GET_ARGS} --install-optional --install-test-deps --install-deb-deps \
		dpkg-dev
