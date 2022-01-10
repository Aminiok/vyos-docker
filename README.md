# vyos-docker
## Running VyOS in docker

```console 
docker run -d   -v /lib/modules:/lib/modules -v vyos-config:/opt/vyatta/etc/config/ --privileged  --network local-net --sysctl net.ipv6.conf.all.disable_ipv6=0 --restart always -p 179:179  -p 8000:8080  --name vyos-router -d afla/vyos:1.4
```

## Running VyOS in Kubernetes

```console 
kubectl apply -f vyos.yaml
```
