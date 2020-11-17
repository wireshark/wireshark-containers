FROM fedora
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN chmod +x rpm-setup.sh \
	&& dnf upgrade -y \
	&& ./rpm-setup.sh --install-optional -y
