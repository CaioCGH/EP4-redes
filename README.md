# POC CVE-2018-15473 exploit

Adaptado de https://github.com/Rhynorater/CVE-2018-15473-Exploit

Para rodar este exploit é necessário ter instalado:

-docker
-docker compose

## servidor ssh

Vamos começar puxando do DockerHub uma imagem que tem uma versão antiga (6.6) do SSH num Ubuntu antigo:
Pode demorar até alguns minutos para baixar tudo, mas só precisa baixar uma vez.
```
docker pull dockerbase/openssh-server
```
Contruímos a nossa imagem e subimos o container
```
docker-compose build
docker-compose up
```
Em outro terminal, abrimos a shell do servidor
```
docker exec -it server /bin/sh
```
Verificamos que a versão do SSH é antiga
```
ssh -V
```
Criamos um usuário
```
adduser mark
```
Insira a senha duas vezes para terminar o cadastro. 
Iniciamos o servidor ssh
```
/etc/init.d/ssh start
```
Descubra o IP com `ip a` e tente se conectar
do terminal hospedeiro ao server com o usuário que acabou de criar.
```
ssh mark@server
```


## atacante 

Na pasta `attacker`, só precisamos 
```
docker-compose build
docker-compose up
```

```
```
E entramos dentro do container
```
docker exec -it attacker /bin/sh
```

Podemos testar a conexão entre o attacker e o server (ssshhh, ele ainda não suspeita de nada)
```
ping server
```
Aí já podemos lançar os ataques:
```
./single_attack.sh
./attack.sh
```
