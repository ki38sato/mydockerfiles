FROM python:3.6.1-slim

ARG PYTHON_LAMBDA_LOCAL_VERSION=0.1.6
ARG LAMBDA_UPLOADER_VERSION=1.3.0
ARG DIRENV_VERSION=2.17.0
ARG PECO_VERSION=0.5.3
ARG GHQ_VERSION=0.8.0

ADD requirements.txt requirements.txt

RUN set -ex \
	&& pip install python-lambda-local==v$PYTHON_LAMBDA_LOCAL_VERSION \
	&& pip install lambda-uploader==$LAMBDA_UPLOADER_VERSION \
	&& pip install --no-cache-dir -r requirements.txt \
	&& mkdir /data \
	&& mkdir -p /direnv/bin \
	&& apt-get update \
	&& apt-get install -y unzip zip gzip curl git groff \
	&& rm -rf /var/lib/apt/lists/* \
	&& curl -fSL -o /direnv/bin/direnv https://github.com/direnv/direnv/releases/download/v${DIRENV_VERSION}/direnv.linux-amd64 \
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
	&& apt-get -y --purge remove unzip

ENV PATH /direnv/bin:/peco/bin:/ghq/bin:$PATH

WORKDIR /data

CMD ["/bin/bash"]
