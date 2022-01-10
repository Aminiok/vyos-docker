# vyos-docker

Docker hub link: https://hub.docker.com/repository/docker/afla/vyos


## Running VyOS in docker

Create the vyos container:

```console 
~]# docker run -d   -v /lib/modules:/lib/modules -v vyos-config:/opt/vyatta/etc/config/ --privileged  --network local-net --sysctl net.ipv6.conf.all.disable_ipv6=0 --restart always -p 179:179  -p 8000:8080  --name vyos-router -d afla/vyos:1.4
```

Connect to the vyos container:

```console
~]# docker exec -it vyos-router vbash
vbash-4.1# su vyos
```

Operation commands:

```console
vyos@vyos:/$ show interfaces
Codes: S - State, L - Link, u - Up, D - Down, A - Admin Down
Interface        IP Address                        S/L  Description
---------        ----------                        ---  -----------
eth0             172.19.0.2/16                     u/u
lo               127.0.0.1/8                       u/u
                 ::1/128
```

Configuration:

```console
vyos@vyos:/$ configure
vyos@vyos# set system host-name test
[edit]
vyos@vyos# commit
[edit]
vyos@vyos# save
Saving configuration to '/config/config.boot'...
Done
[edit]
```

## Running VyOS in Kubernetes

```console 
kubectl apply -f vyos.yaml
```
