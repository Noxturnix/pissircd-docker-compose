FROM ubuntu:20.04

ENV TERM="vt100"

RUN apt update -y && \
    DEBIAN_FRONTEND="noninteractive" apt install -y wget git curl gcc make libssl-dev file build-essential autotools-dev automake pkg-config && \
    rm -rf /var/lib/apt/lists/*

RUN groupadd -r pissircd && useradd -r -m -g pissircd pissircd

RUN git clone https://github.com/pissnet/pissircd pissircd && \
    chown -R pissircd:pissircd pissircd

USER pissircd

WORKDIR /pissircd

RUN ./Config && \
    make && \
    make install

WORKDIR /home/pissircd/unrealircd

USER root

RUN rm -rf /pissircd && \
    rm source

USER pissircd

VOLUME [ "/home/pissircd/unrealircd/data" ]

CMD [ "bin/unrealircd", "-F" ]
