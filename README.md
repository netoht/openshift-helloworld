- [Treinamento RoadShow](http://training.runcloudrun.com/roadshow/)
- [Documentação Openshift Origin](https://docs.openshift.org/latest/getting_started/administrators.html)

## Executando o Openshift Origin em Docker

Pré requisito: ter o docker instalado

PS: Só funciona em CentOS, Fedora ou RedHat Linux

```sh
docker run -d --name "origin" \
        --privileged --pid=host --net=host \
        -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys -v /var/lib/docker:/var/lib/docker:rw \
        -v /var/lib/origin/openshift.local.volumes:/var/lib/origin/openshift.local.volumes \
        openshift/origin start --public-master=192.168.99.100

```

This command:

- starts OpenShift listening on all interfaces on your host (0.0.0.0:8443),
- starts the web console listening on all interfaces at /console (0.0.0.0:8443),
- launches an etcd server to store persistent data, and
- launches the Kubernetes system components.

## Na sua VM

```sh
# adicionar no hosts
127.0.0.1 http://openshift.com.br

# baixe o openshift origin
https://github.com/openshift/origin/releases

# execute o comando abaixo para iniciar
export PATH=$(pwd):$PATH
sudo ./openshift start --public-master=http://openshift.com.br
# pare a execução

# setando variáveis do kubernetes
export KUBECONFIG=`pwd`/openshift.local.config/master/admin.kubeconfig
export CURL_CA_BUNDLE=`pwd`/openshift.local.config/master/ca.crt
sudo chmod +r `pwd`/openshift.local.config/master/admin.kubeconfig

# execute novamente o openshift
sudo ./openshift start --public-master=http://openshift.com.br
```

## Acessando o Openshift Origin

```
# Acessando o painel
http://openshift.com.br

Login: test
Pass:  test

Login: system
Pass: admin
```

## Acessando o Openshift Origin via `cli`

```sh
# logando
oc login https://localhost:8443

# criando um projeto
oc new-project helloworld

# Alterando o uso para o projeto criado
oc project helloworld

# Criando uma aplicação
oc new-app kubernetes/guestbook

# 

```
