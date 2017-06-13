FROM golang:1.8.3

ARG DIRENV_VERSION=2.11.3
ARG PECO_VERSION=0.5.1
ARG GHQ_VERSION=0.7.4

COPY requirements.txt requirements.txt

RUN set -ex \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends unzip curl git groff jq \
	&& rm -rf /var/lib/apt/lists/* \
	&& curl https://raw.githubusercontent.com/apex/apex/master/install.sh | sh \
	&& curl https://bootstrap.pypa.io/get-pip.py | python \
	&& pip install --no-cache-dir -r requirements.txt \
	&& mkdir -p /direnv/bin \
	&& curl -fSL -o /direnv/bin/direnv https://github.com/zimbatm/direnv/releases/download/v${DIRENV_VERSION}/direnv.linux-amd64 \
	&& chmod +x /direnv/bin/direnv \
	&& mkdir -p /peco/bin \
	&& curl -fSL -o peco_linux_amd64.tar.gz https://github.com/peco/peco/releases/download/v${PECO_VERSION}/peco_linux_amd64.tar.gz \
	&& tar xzf peco_linux_amd64.tar.gz \
	&& mv peco_linux_amd64/peco /peco/bin/peco \
	&& rm -rf peco_linux_amd64* \
	&& mkdir -p /ghq/bin \
	&& curl -fSL -o /tmp/ghq_linux_amd64.zip https://github.com/motemen/ghq/releases/download/v${GHQ_VERSION}/ghq_linux_amd64.zip \
	&& cd /tmp \
	&& unzip /tmp/ghq_linux_amd64.zip \
	&& mv /tmp/ghq /ghq/bin/ghq \
	&& rm -rf /tmp/* \
	&& apt-get -y --purge remove unzip \
	&& mkdir /ref

ENV PATH /direnv/bin:/peco/bin:/ghq/bin:/ref/bin:$PATH
ENV GOPATH /ref:/data

RUN go get github.com/mattn/gom
RUN set -ex \
	&& go get github.com/Masterminds/glide \
	&& go install github.com/Masterminds/glide
RUN go get github.com/tools/godep

WORKDIR /data

CMD ["/bin/bash"]
