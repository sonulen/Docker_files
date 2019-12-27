# В качестве базового образа для сборки используем gcc:latest
FROM ubuntu:18.04

ENV TZ=Europe/Moscow

# Update
RUN apt-get update && apt-get install -y software-properties-common && \
    add-apt-repository ppa:inkscape.dev/stable && apt-get update

# Install git make cmake
RUN apt-get install -y git cmake make

RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

# Install texlive
RUN add-apt-repository ppa:jonathonf/texlive-2018 && \
    apt-get update && \
    apt-get -o Dpkg::Options::="--force-overwrite" install -y --allow-unauthenticated && \ 
    apt install -y texlive texlive-lang-cyrillic texlive-lang-english texlive-latex-extra \
    cm-super texlive-xetex texlive-generic-extra texlive-luatex

# Install all deps
RUN apt-get install -y inkscape
RUN apt-get install -y plantuml wget

RUN wget http://sourceforge.net/projects/plantuml/files/plantuml.jar/download -O /usr/share/plantuml/plantuml.jar && \
    apt-get install -y fonts-lmodern && \
    wget http://ru.legionfonts.com/download/gost-type-a-italic && \
    mkdir -p ~/.local/share/fonts/ && \
    unzip -o gost-type-a-italic -d ~/.local/share/fonts/ && \
    rm gost-type-a-italic && \
    wget http://mirrors.ctan.org/install/macros/latex/contrib/glossaries.tds.zip && \
    wget http://mirrors.ctan.org/install/macros/latex/contrib/glossaries-extra.tds.zip && \
    unzip -o glossaries.tds.zip -d /usr/share/texlive/texmf-dist/ && \
    unzip -o glossaries-extra.tds.zip -d /usr/share/texlive/texmf-dist/ && \
    texhash && \
    rm glossaries.tds.zip && \
    rm glossaries-extra.tds.zip
