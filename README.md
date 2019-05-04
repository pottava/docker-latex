# Dockerized [LaTeX](https://www.latex-project.org/)

[![pottava/latex](http://dockeri.co/image/pottava/latex)](https://hub.docker.com/r/pottava/latex/)

## Supported tags and respective `Dockerfile` links:

・latest ([versions/2019/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2019/base/Dockerfile))  
・2019 ([versions/2019/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2019/base/Dockerfile))  
・2019jp ([versions/2019/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/209/jp/Dockerfile))  
・2018 ([versions/2018/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2018/base/Dockerfile))  
・2018jp ([versions/2018/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2018/jp/Dockerfile))  
・2017 ([versions/2017/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2017/base/Dockerfile))  
・2017jp ([versions/2017/base/Dockerfile](https://github.com/pottava/docker-latex/blob/master/versions/2017/jp/Dockerfile))  

## Usage

```console
docker run --rm -it -v $(pwd):/work pottava/latex:2019 latex sample.tex
docker run --rm -it -v $(pwd):/work pottava/latex:2019 dvipdfmx sample.dvi
```
