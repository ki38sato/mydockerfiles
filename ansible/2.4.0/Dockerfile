FROM python:3.6.4-slim

ARG ANSIBLE_VERSION=2.4.0
ARG DIRENV_VERSION=2.13.3
ARG PECO_VERSION=0.5.2
ARG GHQ_VERSION=0.8.0

ADD requirements.txt requirements.txt

RUN set -ex \
	&& buildDeps=' \
		gcc \
		python-dev \
		libffi-dev \
		libssl-dev \
	' \
	&& apt-get update \
	&& apt-get install -y --no-install-recommends $buildDeps \
	&& apt-get install -y openssh-server sshpass \
	&& rm -rf /var/lib/apt/lists/* \
	&& pip install boto boto3 \
	&& pip install ansible==$ANSIBLE_VERSION \
	&& apt-get purge -y --auto-remove $buildDeps \
	&& pip install --no-cache-dir -r requirements.txt \
	&& mkdir -p /direnv/bin \
  && apt-get update \
  && apt-get install -y --no-install-recommends unzip curl git jq zip \
  && rm -rf /var/lib/apt/lists/* \
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
	&& rm -rf /tmp/*

ENV PATH /direnv/bin:/peco/bin:/ghq/bin:$PATH

WORKDIR /data

CMD ["/bin/bash"]
