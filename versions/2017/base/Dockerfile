# LaTeX
# docker run --rm -it pottava/latex:2017
# docker run --rm -it -v $(pwd):/work pottava/latex:2017 latex sample.tex
# docker run --rm -it -v $(pwd):/work pottava/latex:2017 dvipdfmx sample.dvi

FROM alpine:3.7

ENV GLIBC_VERSION=2.27-r0 \
    PATH=/usr/local/texlive/2017/bin/x86_64-linux:$PATH

RUN apk --no-cache add wget perl make
RUN apk --no-cache add --virtual build-deps bash curl libgcc \
    && GLIBC_DL_URL="https://github.com/andyshinn/alpine-pkg-glibc/releases/download/${GLIBC_VERSION}" \
    && curl --location --silent --show-error -O ${GLIBC_DL_URL}/glibc-${GLIBC_VERSION}.apk \
    && curl --location --silent --show-error -O ${GLIBC_DL_URL}/glibc-bin-${GLIBC_VERSION}.apk \
    && curl --location --silent --show-error -O ${GLIBC_DL_URL}/glibc-i18n-${GLIBC_VERSION}.apk \
    && apk add --allow-untrusted glibc-${GLIBC_VERSION}.apk \
       glibc-bin-${GLIBC_VERSION}.apk glibc-i18n-${GLIBC_VERSION}.apk \
    && /usr/glibc-compat/sbin/ldconfig /lib /usr/glibc-compat/lib \
    && /usr/glibc-compat/bin/localedef -i en_US -f UTF-8 en_US.UTF-8 \
    && apk del --purge -r build-deps glibc-i18n \
    && rm -rf glibc-*.apk

RUN apk --no-cache add icu-libs --repository http://dl-3.alpinelinux.org/alpine/edge/main \
    && apk --no-cache add --virtual build-deps xz fontconfig-dev \
    && cd /tmp \
    && wget --quiet ftp://tug.org/historic/systems/texlive/2017/install-tl-unx.tar.gz \
    && tar --strip-components=1 -xf install-tl-unx.tar.gz \
    && printf "%s\n" \
      "selected_scheme scheme-minimal" \
      "option_doc 0" \
      "option_doc 0" \
      "option_src 0" \
      "option_letter 0" \
      "portable 0" \
      > /tmp/texlive.profile \
    && ./install-tl --profile=/tmp/texlive.profile \
    && tlmgr install collection-basic collection-latex latexmk \
    && ( tlmgr install xetex || exit 0 ) \
    && apk del --purge -r build-deps icu-libs \
    && rm -rf /tmp/*

CMD ["latex", "-help"]
