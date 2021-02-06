FROM lopsided/archlinux:devel
LABEL maintainer "Ben Wolsieffer <benwolsieffer@gmail.com>"

ARG ARCH="x86_64"
ARG BUILD_UID="1000"

COPY pacman-${ARCH}.conf /etc/pacman.conf
COPY mirrorlist-${ARCH} /etc/pacman.d/mirrorlist
COPY docker-build-package /usr/local/bin

RUN pacman -Syu --noconfirm \
         bzr \
         git \
         mercurial \
         namcap \
         svn \
    && rm -f \
         /var/cache/pacman/pkg/* \
         /var/lib/pacman/sync/* \
         /etc/pacman.d/mirrorlist.pacnew \
    && mkdir /pkg

ENV BUILD_UID ${BUILD_UID}
ENTRYPOINT ["/usr/local/bin/docker-build-package"]
