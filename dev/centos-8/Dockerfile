FROM centos:8
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN chmod +x rpm-setup.sh \
	&& dnf -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm \
	&& dnf upgrade -y \
	&& ./rpm-setup.sh --install-optional -y
