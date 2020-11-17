FROM centos:8
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
# PowerTools is the CentOS name for CodeReady, where -devel packages live
# Devel is a CentOS repository with some extra -devel packages not (yet?) in RHEL
RUN chmod +x rpm-setup.sh \
	&& dnf -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm \
	&& dnf upgrade -y \
	&& dnf -y install dnf-plugins-core \
	&& dnf config-manager --enable PowerTools \
	&& dnf config-manager --enable Devel \
	&& ./rpm-setup.sh --install-optional -y
