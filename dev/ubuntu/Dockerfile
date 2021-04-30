# To do:
# - Remove clang-11. No longer used in master.
# - Remove unversioned clang-tools.

FROM ubuntu:20.04
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /debian-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/debian-setup.sh /debian-setup-3.4.sh
ENV COMMON_APT_GET_ARGS="--yes --no-install-recommends"
# NOTE: Ensure that we provide clang-[xy] versions used in .gitlab-ci.yml in each active Wireshark branch.
RUN export DEBIAN_FRONTEND="noninteractive" DEBCONF_NONINTERACTIVE_SEEN=true \
	&& printf "tzdata tzdata/Areas select Etc\ntzdata tzdata/Zones/Etc select UTC" | debconf-set-selections \
	&& chmod -v +x debian-setup*.sh \
	&& apt-get update \
	&& apt-get install build-essential gnupg apt-utils ca-certificates ${COMMON_APT_GET_ARGS} \
	&& apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6084F3CF814B57C1CF12EFD515CF4D18AF4F7421 \
	&& echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-12 main" > /etc/apt/sources.list.d/clang-12.list \
	&& echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-11 main" > /etc/apt/sources.list.d/clang-11.list \
	&& echo "deb http://apt.llvm.org/focal/ llvm-toolchain-focal-10 main" > /etc/apt/sources.list.d/clang-10.list \
	&& apt-get update \
	&& apt-get upgrade --yes \
	&& ./debian-setup-3.4.sh ${COMMON_APT_GET_ARGS} --install-optional --install-test-deps --install-deb-deps \
	&& ./debian-setup-master.sh ${COMMON_APT_GET_ARGS} --install-optional --install-deb-deps --install-test-deps \
		awscli \
		build-essential \
		ccache \
		clang-10 \
		clang-11 \
		clang-12 \
		clang-tools \
		clang-tools-12 \
		colorized-logs \
		cppcheck \
		curl \
		doxygen \
		fakeroot \
		gcc-10 g++-10 \
		graphviz \
		jq \
		lintian \
		locales \
		python-pygments \
		python3-pytest-xdist \
		shellcheck \
		sloccount \
		zip \
	&& locale-gen en_US.UTF-8 \
	&& dpkg-query -Wf '${Installed-Size}\t${Package}\n' | sort -rn | head -n 50 \
	&& rm -rf /var/lib/apt/lists/
