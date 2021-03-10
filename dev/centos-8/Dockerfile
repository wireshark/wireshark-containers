FROM centos:8
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
# PowerTools is the CentOS name for CodeReady, where -devel packages live
# Devel is a CentOS repository with some extra -devel packages not (yet?) in RHEL
ENV COMMON_YUM_ARGS="--assumeyes --setopt=install_weak_deps=False"
RUN chmod -v +x rpm-setup*.sh \
	&& dnf -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm \
	&& dnf upgrade -y \
	&& dnf -y install dnf-plugins-core \
	&& dnf repolist all \
	&& dnf config-manager --enable powertools \
	&& dnf config-manager --enable devel \
	&& ./rpm-setup-3.4.sh ${COMMON_YUM_ARGS} --install-optional \
	&& ./rpm-setup-master.sh ${COMMON_YUM_ARGS} --install-optional \
		ccache \
	&& rpm -qa --queryformat '%10{size}\t%-25{name}\n' | sort -rn | head -n 50 \
	&& dnf clean all
