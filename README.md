- [Treinamento RoadShow](http://training.runcloudrun.com/roadshow/)
- [Documentação Openshift Origin](https://docs.openshift.org/latest/getting_started/administrators.html)

## Executando o Openshift Origin em Docker

```sh
docker run -d --name "origin" \
        --privileged --pid=host --net=host \
        -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys -v /var/lib/docker:/var/lib/docker:rw \
        -v /var/lib/origin/openshift.local.volumes:/var/lib/origin/openshift.local.volumes \
        openshift/origin start

```

This command:

- starts OpenShift listening on all interfaces on your host (0.0.0.0:8443),
- starts the web console listening on all interfaces at /console (0.0.0.0:8443),
- launches an etcd server to store persistent data, and
- launches the Kubernetes system components.

## Acessando o Openshift Origin

```
https://192.168.99.100:8443/
```
