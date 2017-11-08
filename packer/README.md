Packer Local Environment
---
packer container with direnv/peco/ghq

version combination history
---
|version|PACKER_VERSION|ANSIBLE_VERSION|DIRENV_VERSION|PECO_VERION|GHQ_VERSION|
|---|---|---|---|---|---|
|1.1.1|1.1.1|?(2.3.0)|2.13.1|0.5.1|0.8.0|

```
docker build -t packer-dev:1.1.1 base/ --build-arg DIRENV_VERSION=2.13.1 --build-arg PECO_VERSION=0.5.1 --build-arg GHQ_VERSION=0.8.0
```

```
$ docker run -it -v "/Users/home/.aws:/root/.aws" -v $PWD:/opt -w /opt -e "AWS_REGION=ap-northeast-1" -e "AWS_PROFILE=user-profile" packer-dev:1.1.1 build -var "mfa_code=123456" /path/to/template.json
```