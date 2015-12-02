FROM fedora:22
MAINTAINER Yoshimasa Tanabe <lanabe.lanabe at gmail.com>

RUN echo "fastestmirror=1" >> /etc/dnf/dnf.conf

RUN dnf -y update
RUN dnf -y reinstall glibc-common
RUN dnf -y install haskell-platform
RUN dnf clean all

ENV LANG ja_JP.utf8

RUN cabal update
RUN cabal install cabal-install

WORKDIR /opt/pandoc
RUN cabal sandbox init
RUN cabal install pandoc
RUN ln -s /opt/pandoc/.cabal-sandbox/bin/pandoc /usr/local/bin/pandoc
RUN cabal install pandoc-crossref
RUN ln -s /opt/pandoc/.cabal-sandbox/bin/pandoc-crossref /usr/local/bin/pandoc-crossref
