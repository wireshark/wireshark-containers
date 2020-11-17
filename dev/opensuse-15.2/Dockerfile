FROM opensuse/leap:15.2
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN chmod +x rpm-setup.sh \
	&& zypper --non-interactive install update-desktop-files \
	&& ./rpm-setup.sh --install-optional ruby \
	&& gem install asciidoctor -v 2.0.10 --no-ri --no-rdoc
