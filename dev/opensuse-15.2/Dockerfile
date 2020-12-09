FROM opensuse/leap:15.2
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
RUN chmod -v +x rpm-setup*.sh \
	&& zypper --non-interactive install update-desktop-files \
	&& ./rpm-setup-3.4.sh --install-optional \
	&& ./rpm-setup-master.sh --install-optional \
		cmake \
		ruby \
	&& gem install asciidoctor -v 2.0.10 --no-ri --no-rdoc
