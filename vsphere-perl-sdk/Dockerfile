#
FROM ubuntu:16.04
ARG SDK=VMware-vSphere-Perl-SDK-6.0.0-3561779.x86_64
ARG SDK_ARCHIVE=${SDK}.tar.gz
ARG SDK_PATCH=${SDK}.patch
MAINTAINER Tim Lapawa <docker@lapawa.de>
WORKDIR /tmp

# copy vsphere perl sdk installer into image
ADD ${SDK}* /tmp/
COPY $SDK_PATCH /tmp

# get prerequisites for installer from ubuntu package repository
RUN apt-get update \
&&  apt-get install --yes --no-install-recommends \
	apt-utils \
	build-essential \
	iputils-ping \
	kmod \
	libterm-readline-perl-perl \
&&  apt-get install --yes --no-install-recommends \
	perl-doc \
	libarchive-zip-perl \
	libssl-dev \
	libclass-data-inheritable-perl \
	libclass-methodmaker-perl \
	libcrypt-openssl-rsa-perl \
	libcrypt-ssleay-perl \
	libcrypt-x509-perl \
	libdata-dump-perl \
	libdevel-stacktrace-perl \
	libexception-class-perl \
	libpath-class-perl \
	libtry-tiny-perl \
	libuuid-perl \
	libpath-class-perl \
	libsoap-lite-perl \
	libsocket6-perl \
	libxml-sax-perl \
	libxml-namespacesupport-perl \
	libxml-libxml-perl \
	libmodule-build-perl \
	libnet-inet6glue-perl \
&&  cpan \
	BINGOS/ExtUtils-MakeMaker-6.96.tar.gz \
	GAAS/libwww-perl-5.837.tar.gz \
	GBARR/libnet-1.22.tar.gz \
	LEONT/Module-Build-0.4205.tar.gz \
	PERLER/UUID-Random-0.04.tar.gz \
&&  cd /tmp && patch -p0 0< ${SDK_PATCH} \
&&  /tmp/vmware-vsphere-cli-distrib/vmware-install.pl --default \
&&  apt-get -y purge \
	apt-utils \
	build-essential \
	dh-make-perl \
	iputils-ping \
	kmod \
&&  apt-get clean && apt-get autoremove -y \
&&  rm -rf /root/.cpan \
	/tmp/cpan_install*.txt \
	/tmp/${SDK_PATCH} \
	/tmp/vmware-vsphere-cli-distrib


CMD ["/bin/bash"]