# CSUIVI

### Installation for development

#### Docker

| Name                 	| URL                                          	| Tested with 	|
|----------------------	|----------------------------------------------	|-------------	|
| Docker               	| https://docs.docker.com/engine/installation/ 	| 17.09.0-ce  	|
| Docker Compose       	| https://docs.docker.com/compose/install/     	| 1.16.1      	|

#### Service list

* apache
* mysql
* adminer
* maildev

#### Start the project

```shell
make up
make down
```

With Traefik proxy, if you do not have a global Traefik proxy for your Docker environment

```shell
make up-with-traefik
make down-with-traefik
```

Add to /etc/hosts these domains, point them to Traefik proxy IP or 127.0.0.1

On Windows 7, use the IP of the Docker VM created by docker-machine  

```
csuivi.local part.csuivi.local pro.csuivi.local orest.csuivi.local scout.csuivi.local maildev.csuivi.local adminer.csuivi.local
```

Optional

```
u2.csuivi.local u3.csuivi.local u5.csuivi.local
```

#### Notes for Windows
You need `make` & `printf` to use Makefile, you can install with scoop.

`printf` is provided with `busybox`

In PowerShell:
```
iex (new-object net.webclient).downloadstring('https://get.scoop.sh')
scoop install make busybox
```

##### Scoop behind proxy

```
# If you want to use a proxy that isn't already configured in Internet Options
[net.webrequest]::defaultwebproxy = new-object net.webproxy "http://proxy.example.org:8080"

# If you want to use the Windows credentials of the logged-in user to authenticate with your proxy
[net.webrequest]::defaultwebproxy.credentials = [net.credentialcache]::defaultcredentials

# If you want to use other credentials (replace 'username' and 'password')
[net.webrequest]::defaultwebproxy.credentials = new-object net.networkcredential 'username', 'password'
```
