FROM fedora
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
ENV COMMON_DNF_ARGS="--assumeyes --setopt=install_weak_deps=False"
RUN chmod -v +x rpm-setup*.sh \
	&& dnf upgrade -y \
	&& ./rpm-setup-3.4.sh ${COMMON_DNF_ARGS} --install-optional \
	&& ./rpm-setup-master.sh ${COMMON_DNF_ARGS} --install-optional --install-rpm-deps \
		ccache \
	&& rpm -qa --queryformat '%10{size}\t%-25{name}\n' | sort -rn | head -n 50 \
	&& yum clean all
