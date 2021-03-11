FROM centos:7
# This is used in the master and release branches, so we need to make sure
# the dependencies for all of those branches are installed.
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
# release-3.4 requires Bison
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
# master-3.2 requires Bison and QtSVG
ADD https://gitlab.com/wireshark/wireshark/-/raw/master-3.2/tools/rpm-setup.sh /rpm-setup-3.2.sh
ENV COMMON_YUM_ARGS="--assumeyes --setopt=install_weak_deps=False"
RUN chmod -v +x rpm-setup*.sh \
	&& yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
	&& yum upgrade -y \
	&& ./rpm-setup-3.2.sh ${COMMON_YUM_ARGS} --install-optional \
	&& ./rpm-setup-3.4.sh ${COMMON_YUM_ARGS} --install-optional \
	&& ./rpm-setup-master.sh ${COMMON_YUM_ARGS} --install-optional \
		ccache \
		rpm-build \
	&& rpm -qa --queryformat '%10{size}\t%-25{name}\n' | sort -rn | head -n 50 \
	&& yum clean all
