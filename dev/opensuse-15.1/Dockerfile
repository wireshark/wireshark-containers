FROM opensuse/leap:15.1
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN chmod +x rpm-setup.sh \
	&& zypper --non-interactive install update-desktop-files \
	&& ./rpm-setup.sh --install-optional ruby \
	&& gem install asciidoctor -v 1.5.8 --no-ri --no-rdoc
