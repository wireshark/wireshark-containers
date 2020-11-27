FROM ubuntu:18.04
ADD https://gitlab.com/wireshark/wireshark/-/raw/master/tools/debian-setup.sh /debian-setup-master.sh
ADD https://gitlab.com/wireshark/wireshark/-/raw/release-3.4/tools/debian-setup.sh /debian-setup-3.4.sh
RUN chmod -v +x debian-setup*.sh \
	&& apt-get update \
	&& apt-get install gnupg apt-utils ca-certificates -y --no-install-recommends \
	&& echo "deb https://apt.llvm.org/bionic/ llvm-toolchain-bionic-10 main" > /etc/apt/sources.list.d/clang10.list \
	&& apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6084F3CF814B57C1CF12EFD515CF4D18AF4F7421 \
	&& apt-get update \
	&& apt-get upgrade -y \
	&& ./debian-setup-3.4.sh --install-optional --install-test-deps -y --install-deb-deps \
	&& ./debian-setup-master.sh -y --install-optional --install-deb-deps --install-test-deps \
		--no-install-recommends build-essential fakeroot \
		python3-pytest-xdist locales \
		gcc-7 g++-7 \
		clang-10 \
		cppcheck clang-tools python-pygments \
		ccache \
		lintian \
	&& rm -rf /var/lib/apt/lists/
