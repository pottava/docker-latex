# LaTeX with Japanese
# docker run --rm -it -v $(pwd):/work pottava/latex:2018jp uplatex sample.tex
# docker run --rm -it -v $(pwd):/work pottava/latex:2018jp dvipdfmx sample.dvi

FROM pottava/latex:2018

RUN apk --no-cache add --virtual build-deps wget perl \
    && tlmgr install \
      collection-latexrecommended collection-fontsrecommended \
      collection-latexextra collection-langjapanese \
    && fc-cache -fv \
    && apk del --purge -r build-deps
