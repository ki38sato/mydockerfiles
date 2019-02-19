ansible by docker
---
ansible container with direnv/peco/ghq

version combination history
---
|version|ANSIBLE_VERSION|DIRENV_VERSION|PECO_VERION|GHQ_VERSION|
|---|---|---|---|---|
|2.4.0|2.4.0|2.17.0|0.5.2|0.8.0|
|2.7.0|2.7.0|2.17.0|0.5.3|0.8.0|

```
docker build -t ansible-dev:2.7.0 base/ --build-arg ANSIBLE_VERSION=2.7.0 --build-arg DIRENV_VERSION=2.17.0 --build-arg PECO_VERSION=0.5.3 --build-arg GHQ_VERSION=0.8.0
```
