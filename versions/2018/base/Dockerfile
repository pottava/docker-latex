# LaTeX
# docker run --rm -it pottava/latex:2018
# docker run --rm -it -v $(pwd):/work pottava/latex:2018 latex sample.tex
# docker run --rm -it -v $(pwd):/work pottava/latex:2018 dvipdfmx sample.dvi

FROM alpine:3.9

ENV PATH=/usr/local/texlive/2018/bin/x86_64-linuxmusl:$PATH

WORKDIR /tmp
RUN apk --no-cache add ghostscript
RUN apk --no-cache add --virtual build-deps icu-libs xz wget make perl \
    && wget --quiet ftp://tug.org/historic/systems/texlive/2018/install-tl-unx.tar.gz \
    && tar --strip-components=1 -xf install-tl-unx.tar.gz \
    && printf "%s\n" \
      "selected_scheme scheme-minimal" \
      "option_doc 0" \
      "option_src 0" \
      "option_letter 0" \
      "portable 0" \
      > /tmp/texlive.profile \
    && ./install-tl --profile=/tmp/texlive.profile \
    && tlmgr install collection-basic collection-latex latexmk \
    && ( tlmgr install xetex || exit 0 ) \
    && fc-cache -fv \
    && apk del --purge -r build-deps \
    && rm -rf /tmp/* /usr/share/perl5 /usr/lib/perl5

WORKDIR /work
CMD ["latex", "-help"]
