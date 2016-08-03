Local Development Docker Container
---

- ansible + direnv + peco + ghq
- terraform + direnv + peco + ghq
- lambda + direnv + peco + ghq
- hubot + direnv

Docker Usage
---
```
docker run -it --rm --name terraform -v "<data_path>":"/data" -v "<docker_home_path>":"/root" terraform /bin/bash
```
- data_path: terraform data path
- docker_home_path: docker user home for direnv

Files
---
```
<docker user home>
    .bashrc
    .gitconfig
```

.bashrc
```
eval "$(direnv hook bash)"

alias g='cd $(ghq list -p | peco)'
```


.gitconfig
```
[ghq]
    root = <GIT ROOT>
```
