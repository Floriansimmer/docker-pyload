# docker-pyload
pyLoad Docker-Image with preconfigured minimal config and the Next theme

Not actively maintained !

![pyload](https://github.com/pyload/pyload/raw/master/media/banner.png)

## Description

pyLoad is a free and open source downloader for 1-click-hosting sites like rapidshare.com or uploaded.to. It supports link decryption as well as all important container formats.

https://github.com/pyload/pyload

## Usage
    docker create --name=pyload  \
      -v <path to downloads>:/downloads  \
      -v <path to config>:/config   \
      -e PGID=<gid> -e PUID=<uid>  \
      -p 8000:8000  \
      -p 7227:7227  \
	  -p 9666:9666 Floriansimmer/docker-pyload


### Get C´n´L running

On Windows run in CMD (as admin)

      netsh interface portproxy add v4tov4 listenport=9666 connectaddress=<NAS/Server IP> connectport=9666 listenaddress=127.0.0.1          

### User / Group Identifiers

Sometimes when using data volumes (`-v` flags) permissions issues can arise between the host OS and the container. We avoid this issue by allowing you to specify the user `PUID` and group `PGID`. Ensure the data volume directory on the host is owned by the same user you specify and it will "just work" ™.

In this instance `PUID=1001` and `PGID=1001`. To find yours use `id user` as below:

```
  $ id <dockeruser>
    uid=1001(dockeruser) gid=1001(dockergroup) groups=1001(dockergroup)
```

## Notes
Default Login is

    pyload
    pyload
	  
* The port 8000 is used for webui
* The port 7227 is used for the api
* The port 9666 is used for click n load plugin
