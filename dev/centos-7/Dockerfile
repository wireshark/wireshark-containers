FROM centos:7
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /
RUN chmod +x rpm-setup.sh \
	&& yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
	&& yum upgrade -y \
	&& ./rpm-setup.sh --install-optional -y
