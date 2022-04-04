# Mifos X 17 - Docker

PRELIMINARIES 

Git pull the repo

```bash
$ git pull https://github.com/helaplus/mifos
```
Create a .env file by copying .env.example
```bash
$ cp .env.example .env
```

Specify the domain, host and email

```bash
$ nano .env
Change PORT, DOMAIN and EMAIL
```

Specify your IP in Nginx.conf

```bash
$ nano nginx/conf.d/app.conf
Change ${your_ip}] to your IP
```

1. Just run Docker compose to get Mifos X 17 up and running. 

```bash
$ docker-compose up
```


2. Login to Mifos using the Web UI with these credentials:

username: mifos
password: password

https://localhost:8443/community-app/#/ (secure web access, but this is a self signed certificate and you will have a warning in your web explorer, just ignore it and continue)


3. As note if you have any issue with the volumes and entry points remove the volumes (be careful, with this we are removing all of them, because it is running in our local DEV, don't do this in Production)
```bash
$ docker stop $(docker ps -a -q)
$ docker rm $(docker ps -a -q)
$ docker volume rm $(docker volume ls -q)
```

Reference 

* http://mifos.org/take-action/get-mifos/#download
* https://mifosforge.jira.com/wiki/spaces/MDZ/pages/92504091/Prerequisite
* https://mifosforge.jira.com/wiki/spaces/docs/pages/74711072/Mifos+X+Installation+on+Linux+-+Ubuntu+Server 
* https://github.com/dmitryint/docker-mifosx
* https://github.com/docker-library/docs/tree/master/mariadb
* https://docs.docker.com/docker-cloud/builds/push-images/
* https://issues.apache.org/jira/secure/ReleaseNote.jspa?version=12340624&styleName=&projectId=12319420&Create=Create&atl_token=A5KQ-2QAV-T4JA-FDED%7C7616978f36b22cf7dc20a899a3cbf9f614960808%7Clin
* https://medium.com/viithiisys/mifos-x-installation-on-linux-ubuntu-server-3843e028ab90

Issues with the reports
* https://stackoverflow.com/questions/37066024/what-is-the-mariadb-dialect-class-name-for-hibernate
* http://sterl.org/2015/09/spring-boot-mariadb/
* http://in.relation.to/2017/02/16/mariadb-dialects/
