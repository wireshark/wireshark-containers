FROM fedora
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN dnf upgrade -y \
	&& chmod +x rpm-setup.sh \
	&& rpm-setup.sh --install-optional -y
