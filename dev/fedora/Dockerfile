FROM fedora
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
RUN chmod -v +x rpm-setup*.sh \
	&& dnf upgrade -y \
	&& ./rpm-setup-3.4.sh --install-optional -y \
	&& ./rpm-setup-master.sh --install-optional -y
