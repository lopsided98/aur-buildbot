FROM lopsided/archlinux:devel
LABEL maintainer "Ben Wolsieffer <benwolsieffer@gmail.com>"

ARG MIRROR_URL="https://mirrors.kernel.org/archlinux/\$repo/os/\$arch"
ARG BUILD_UID="1000"

RUN echo "Server = ${MIRROR_URL}" > /etc/pacman.d/mirrorlist \
    && pacman -Syu --noconfirm \
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

COPY docker-buildpkg /usr/local/bin

ENV BUILD_UID ${BUILD_UID}
ENV MIRROR_URL ${MIRROR_URL}
ENTRYPOINT ["/usr/local/bin/docker-buildpkg"]
