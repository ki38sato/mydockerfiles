Terraform Local Environment
---
terraform container with direnv/peco/ghq

version combination history
---
|version|TERRAFORM_VERSION|DIRENV_VERSION|PECO_VERION|GHQ_VERSION|
|---|---|---|---|---|
|0.6.16|0.6.16|2.8.1|0.3.6|0.7.4|
|0.7.1 - 0.7.10, 0.8.4|0.7.0 - 0.7.10, 0.8.4|2.9.0|0.3.6|0.7.4|
|0.8.5|0.8.5|2.10.0|0.4.7|0.7.4|
|0.8.6|0.8.6|2.10.0|0.4.9|0.7.4|
|0.9.1 - 0.9.11|0.9.1 - 0.9.11|2.10.0|0.5.1|0.7.4|
|0.10.8|0.10.8|2.13.1|0.5.1|0.8.0|
|0.11.1 - 0.11.2|0.11.1 - 0.11.2|2.13.3|0.5.2|0.8.0|

```
docker build -t terraform:0.11.2 base/ --build-arg TERRAFORM_VERSION=0.11.2 --build-arg DIRENV_VERSION=2.13.3 --build-arg PECO_VERSION=0.5.2 --build-arg GHQ_VERSION=0.8.0
```
