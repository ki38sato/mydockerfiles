FROM golang:1.8.1

ARG DIRENV_VERSION=2.10.0
ARG PECO_VERSION=0.5.1
ARG GHQ_VERSION=0.7.4

RUN set -ex \
	&& apt-get update \
	&& apt-get install -y unzip curl git \
	&& rm -rf /var/lib/apt/lists/* \
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

WORKDIR /data

CMD ["/bin/bash"]
