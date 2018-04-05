# Dockerized [LaTeX](https://www.latex-project.org/)

[![pottava/latex](http://dockeri.co/image/pottava/latex)](https://hub.docker.com/r/pottava/latex/)

## Supported tags and respective `Dockerfile` links:

・latest ([versions/2017/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2017/base/Dockerfile))  
・2017 ([versions/2017/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2017/base/Dockerfile))  
・2017jp ([versions/2017/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2017/jp/Dockerfile))  

## Usage

```
$ docker run --rm -it -v $(pwd):/work pottava/latex:2017 latex sample.tex
$ docker run --rm -it -v $(pwd):/work pottava/latex:2017 dvipdfmx sample.dvi
```
