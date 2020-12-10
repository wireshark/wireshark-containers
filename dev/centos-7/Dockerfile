FROM centos:7
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/rpm-setup.sh /rpm-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/master-3.2/tools/rpm-setup.sh /rpm-setup-3.2.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/rpm-setup.sh /rpm-setup-3.4.sh
RUN chmod -v +x rpm-setup*.sh \
	&& yum -y install https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm \
	&& yum upgrade -y \
	&& ./rpm-setup-3.2.sh --install-optional -y \
	&& ./rpm-setup-3.4.sh --install-optional -y \
	&& ./rpm-setup-master.sh --install-optional -y
