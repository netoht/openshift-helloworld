- [Treinamento RoadShow](http://training.runcloudrun.com/roadshow/)
- [Documentação Openshift Origin](https://docs.openshift.org/latest/getting_started/administrators.html)

## Executando o Openshift Origin em Docker
```sh
sudo docker run -d --name "origin" \
        --privileged --pid=host --net=host \
        -v /:/rootfs:ro -v /var/run:/var/run:rw -v /sys:/sys -v /var/lib/docker:/var/lib/docker:rw \
        -v /var/lib/origin/openshift.local.volumes:/var/lib/origin/openshift.local.volumes \
        openshift/origin start
```
