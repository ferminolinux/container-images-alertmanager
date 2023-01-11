# Container Images: Alertmanager

As imagens estão disponíveis através do [GitHubPackages](https://github.com/ferminolinux/container-images-alertmanager/pkgs/container/alertmanager) e no [Docker Hub](https://hub.docker.com/r/ferminolinux/alertmanager).

Você pode utilizar esta imagem em um container com o comando a seguir:

```bash
docker run --name alertmanager -d -p 9093:9093 ferminolinux/alertmanager
```

Você pode iniciar o alertmanager com um arquivo de configurações personalizado

```bash
docker run  \ 
    --name alertmanager \
    -d \
    -p 9093:9093 \
    -v $(pwd)/alertmanager.yml:/usr/local/etc/alertmanager/alertmanager.yml \
    ferminolinux/alertmanager
```
