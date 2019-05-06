FROM slankdev/frr
LABEL maintainer "Taichi MIYA <tmiya@protonmail.ch>"

ARG VERSION="5.0.0"

RUN apt install -y bison flex make gcc
ADD https://mirrors.edge.kernel.org/pub/linux/utils/net/iproute2/iproute2-${VERSION}.tar.xz /iproute2-${VERSION}.tar.xz
RUN xz -d /iproute2-${VERSION}.tar.xz && \
    tar -xf /iproute2-${VERSION}.tar && \
    cd /iproute2-${VERSION} && \
    sed -i /ARPD/d Makefile && \
    sed -i 's/.m_ipt.o//' tc/Makefile && \
    make && \
    make DOCDIR=/usr/share/doc/iproute2-${VERSION} install
