FROM opensuse/leap:15.2
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
ENV COMMON_ZYPPER_ARGS="--no-confirm --no-recommends"
RUN chmod -v +x rpm-setup*.sh \
	&& zypper install ${COMMON_ZYPPER_ARGS} update-desktop-files \
	&& ./rpm-setup-3.4.sh --install-optional \
	&& ./rpm-setup-master.sh --install-optional --install-rpm-deps \
		ccache \
		ruby \
	&& gem install asciidoctor -v 2.0.16 --no-ri --no-rdoc \
	&& rpm -qa --queryformat '%10{size}\t%-25{name}\n' | sort -rn | head -n 50 \
	&& zypper clean --all
