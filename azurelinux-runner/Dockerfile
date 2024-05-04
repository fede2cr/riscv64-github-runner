FROM docker.io/fede2/mariner-riscv64:alpha
VOLUME /runner

RUN groupadd runner && groupadd sudo && \
    useradd -s /bin/bash -g runner -m -k /dev/null runner && \
    usermod -a -G sudo runner && \
    echo "runner ALL = NOPASSWD : ALL" >> /etc/sudoers

#RUN apt-get update && apt-get install -y --no-install-recommends \
#libatomic1 \
#xz-utils \
#wget \
#python3-setuptools \
#python3-pip \
#python3-dev \
#python3-venv \
#git \
#&& \
#apt-get clean && \
#rm -rf /var/lib/apt/lists/*

RUN cd /usr/local/ && wget 'https://unofficial-builds.nodejs.org/download/release/v21.6.2/node-v21.6.2-linux-riscv64.tar.xz' && \
tar xf node-v21.6.2-linux-riscv64.tar.xz && \
rm node-v21.6.2-linux-riscv64.tar.xz

ENV PATH=$PATH:/usr/local/node-v21.6.2-linux-riscv64/bin/

USER runner

CMD ["/usr/local/runner/run.sh"]
