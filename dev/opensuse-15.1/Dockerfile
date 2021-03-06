FROM opensuse/leap:15.1
# This is used in the master and release branches, so we need to make sure
# the dependencies for all of those branches are installed.
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
# release-3.4 requires Bison
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
# master-3.2 requires Bison and QtSVG
ADD https://gitlab.com/wireshark/wireshark/-/raw/master-3.2/tools/rpm-setup.sh /rpm-setup-3.2.sh
ENV COMMON_ZYPPER_ARGS="--no-confirm --no-recommends"
RUN chmod -v +x rpm-setup*.sh \
	&& zypper install ${COMMON_ZYPPER_ARGS} update-desktop-files \
	&& ./rpm-setup-3.2.sh --install-optional \
	&& ./rpm-setup-3.4.sh --install-optional \
	&& ./rpm-setup-master.sh --install-optional \
		ccache \
		cmake \
		ruby \
	&& gem install asciidoctor -v 1.5.8 --no-ri --no-rdoc \
	&& rpm -qa --queryformat '%10{size}\t%-25{name}\n' | sort -rn | head -n 50 \
	&& zypper clean --all