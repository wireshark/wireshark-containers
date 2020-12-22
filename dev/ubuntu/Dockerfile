FROM ubuntu:20.04
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /debian-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/debian-setup.sh /debian-setup-3.4.sh
# NOTE: Ensure that we provide clang-[xy] versions used in .gitlab-ci.yml in each active Wireshark branch.
RUN export DEBIAN_FRONTEND="noninteractive" DEBCONF_NONINTERACTIVE_SEEN=true \
	&& printf "tzdata tzdata/Areas select Etc\ntzdata tzdata/Zones/Etc select UTC" | debconf-set-selections \
	&& chmod -v +x debian-setup*.sh \
	&& apt-get update \
	&& apt-get install gnupg apt-utils ca-certificates -y --no-install-recommends \
	&& apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6084F3CF814B57C1CF12EFD515CF4D18AF4F7421 \
	&& echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-11 main" > /etc/apt/sources.list.d/clang-11.list \
	&& echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-10 main" > /etc/apt/sources.list.d/clang-10.list \
	&& apt-get update \
	&& apt-get upgrade -y \
	&& ./debian-setup-3.4.sh --install-optional --install-test-deps -y --install-deb-deps \
	&& ./debian-setup-master.sh -y --install-optional --install-deb-deps --install-test-deps \
		--no-install-recommends \
		awscli \
		build-essential \
		ccache \
		clang-10 \
		clang-11 \
		clang-tools \
		cppcheck \
		doxygen \
		fakeroot \
		gcc-10 g++-10 \
		graphviz \
		lintian \
		locales \
		python-pygments \
		python3-pytest-xdist \
		shellcheck \
	&& locale-gen en_US.UTF-8 \
	&& rm -rf /var/lib/apt/lists/
