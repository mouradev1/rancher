# Comando de instalação
```
docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  -v /opt/rancher:/var/lib/rancher \
  --privileged \
  --name rancher \
  rancher/rancher:v2.6.3

```

# Comando para o backup rancher

```
docker stop rancher

tar pzcvf /opt/rancher/rancher-backup/rancher-backup.tar.gz /opt/rancher

docker rancher start

```
# Comando de Restore

* Comando para descompacta o backup dentro da sua nova vm

```
tar pzxvf  rancher-backup.tar.gz -C /

```

# Subindo o rancher com a versão atualizada

```
docker run -d --restart=unless-stopped \
  -p 80:80 -p 443:443 \
  -v /opt/rancher:/var/lib/rancher \
  --privileged \
  --name rancher \
  rancher/rancher:v2.6.8

```


# LINKS DA DOCUMENTAÇÕES OFICIAL

* RANCHER -> https://rancher.com/docs/rancher/v2.5/en/installation/other-installation-methods/single-node-docker/

* VAGRANT -> https://www.vagrantup.com