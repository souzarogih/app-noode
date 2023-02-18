<h1>Projeto para uso prático de Docker</h1>

## Docker Hub
[App-Noode](https://hub.docker.com/r/higorsouza/app-noode)

### Build da aplicação
#### Build no docker
`docker build -t souzarogih/app-noode:1.0 .` 

#### Executar a imagem
`docker run -d -p 8081:3000 souzarogih/app-noode:1.0`

#### Logar no docker hub para fazer push
- `docker login -u [user_name]`
- `Insira sua senha`

#### Fazer push de uma imagem para o docker
`docker push higorsouza/app-noode:1.3`

#### Criar uma cópia/tag de uma aplicação
`docker tag souzarogih/app-noode:1.3 higorsouza/app-noode:1.3`

### Compartilhamento de volumes
#### Compartilhar um volume entre host e container com volume | flag -v
`docker run -it -v [volume_host]:[volume_container] ubuntu bash`
```bash
$ docker run -it -v /home/higorsouza:/app ubuntu bash
```

#### Compartilhar um volume entre host e container com bind mount | flag --mount (Mais indicado)
`docker run -it --mount type=bind,source=[volume_host],target=[volume_container] ubuntu bash`
```bash
$ docker run -it --mount type=bind,source=/home/higorsouza,target=/app ubuntu bash
```

### Volumes
#### Listar os volumes
`$ docker volume ls`

#### Criar volume
`$ docker volume create meu-volume`

#### Criar container e compartilhar com volume criado
`docker run -it -v [nome_volume]:[volume_container] ubuntu bash`
```bash
$ docker run -it -v meu-volume:/app ubuntu bash
```
#### Criar container e compartilhar com volume criado 2
```bash
$ docker run -it --mount source=meu-novo-volume,target=/app ubuntu bash
```

#### Remover um volume 
```bash
$ docker volume rm fa98f9d4322f63019501b4efeef26c966f5212d5fb65945b6ca5188078763a12 -f
```

### Usando volumes temporários com tmpfs
```bash
$ docker run -it --tmpfs=/app ubuntu bash
```
```bash
$ docker run -it --mount type=tmpfs,destination=/app ubuntu bash
```

## Redes Docker
### Listar as redes do docker
```bash
$ docker network ls
```

### Excluir uma network
```docker network rm [NETWORK_ID]```
```bash
$ docker network rm 0446a6831984
```

### Criar uma network
```docker network create --driver bridge [NOME_DA_NETWORK]```
```bash
$ docker network create --driver bridge minha-bridge
```

### Criar container com nome
```bash
$ docker run -it --name ubuntu1 --network minha-bridge ubuntu bash 
```

## Outras informações sobre docker
### Caminho com configurações do docker
cd /var/lib/docker

### Fonte de pesquisa
https://www.macoratti.net/19/02/dock_limp1.htm