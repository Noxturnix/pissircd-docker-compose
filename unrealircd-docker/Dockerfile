FROM ubuntu:20.04

ENV TERM="vt100"

RUN apt update -y && \
    apt install -y wget curl gcc make libssl-dev file jq && \
    rm -rf /var/lib/apt/lists/*

RUN groupadd -r unrealircd && useradd -r -m -g unrealircd unrealircd

RUN wget $(curl https://www.unrealircd.org/downloads/list.json -s | jq ".[].Stable.downloads.src" -r) -O unrealircd.tar.gz && \
    tar -xvf unrealircd.tar.gz && \
    rm unrealircd.tar.gz && \
    mv unrealircd* unrealircd && \
    chown -R unrealircd:unrealircd unrealircd

USER unrealircd

WORKDIR /unrealircd

RUN ./Config && \
    make && \
    make install

WORKDIR /home/unrealircd/unrealircd

USER root

RUN rm -rf /unrealircd && \
    rm source

USER unrealircd

VOLUME [ "/home/unrealircd/unrealircd/data" ]

CMD [ "bin/unrealircd", "-F" ]
