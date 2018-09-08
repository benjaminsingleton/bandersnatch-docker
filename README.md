# Bandersnatch PyPI Mirror

This docker-compose file starts a bandersnatch PyPI mirror client according to PEP 381 as well as an nginx web server to serve the packages. This can be used to set up an internal PyPI mirror behind a company/organization firewall, for example. 

## Installation
1. Install and start [Docker](https://docs.docker.com/install/)
2. Download this project: `$ git clone bandersnatch-docker`
3. `$ cd bandersnatch-docker`
4. Start the mirror and the web server: `$ docker-compose up`. Initially, this will take a while to download all the packages from PyPI that are whitelisted. Ensure you have enough disk space for all the packages that will be downloaded.
5. Pip install a package that has been whitelisted: `$ pip install -i http://<host-ip>:8080/simple <package-name>`


## Things to Know
- The default whitelisted packages are all the Anaconda Python packages supported in Python 2.7 and 3.6.
- The default cron job is set to run every hour. Change `bandersnatch/bandersnatchcron` if you'd like a different frequency.

### Docker Cheat Sheet
`docker-compose up`

`docker-compose stop`

`docker-compose down`

`docker build -t bandersnatch-1 .`

`docker run -it bandersnatch-1 bash`

`docker run -d -p 8080:80 bandersnatch-1`

`docker ps`

`docker exec -it <container-name> /bin/bash`

