REM server with Anax included
==================================

This is an complete bundle of the Anax module REM server [canax/remserver](https://github.com/canax/remserver) together with an Anax website. It can be used to quickly start up a standalone REM server for test and development.



Table of content
----------------------------------

* [Install](#install)
    * [Install from Git repo](#install-from-git-repo)
    * [Run Git repo within Docker](#run-git-repo-within-docker)
    * [Run using Docker image](#run-using-docker-image)
    * [Install as an Anax module](#install-as-an-anax-module)
    * [Install on a production server using http](#install-on-a-production-server-using-http)
    * [Install on a production server using http](#install-on-a-production-server-using-http)

* [How to use and documentation](#how-to-use-and-documentation)



Install
----------------------------------

There are a few ways to get the REM server up and rolling.



### Install from Git repo

Download this Git repo.

Install essential tools.

```
make install
```

Point your web browser to `htdocs` and you should see the documentation.



### Run Git repo within Docker

Perform the same steps as in [Install from Git repo](#install-from-git-repo).

Start a docker container that has Apache running. The file `docker-compose.yaml` is prepared with an Anax image that can be used for development and tests.

```
docker-compose up remserver-dev
```

Point your web browser to `http://localhost:10099/htdocs` and you should see the documentation.



### Run using Docker image

There is a Docker image that has the REM server website installed and ready to run.

If you have downloaded this repo you can start it with `docker-compose`. It will use the setup you have in [`docker-compose.yml`](docker-compose.yml).

```
docker-compose up remserver
```

You can start it anywhere you have access to `docker`. Run like this and map the container port 80 to the local host port 10999.

```
docker run -p 10999:80 anax/dev:remserver
```



### Install as an Anax module

If you want the REM server as a Anax module to be installed together with your own Anax installation, then you should install the module itself.

Read more on the module [canax/remserver](https://github.com/canax/remserver).



### Install on a production server using http

This implies setting up its own Apache virtual host to run the website. The Git repo is used as source but copied to the production site, normally on the same machine on `$HOME/htdocs/server-name/`.

First, perform the same steps as in [Install from Git repo](#install-from-git-repo).

Then you setup the local environment on the host, to make it both a development server and a prodution server.

```text
make etc-hosts       # Create a entry in the /etc/hosts for local access.
make site-build      # Create essential directories to run as local website.
make local-publish   # Publish website to local host.
make virtual-host    # Create files for the virtual host http configuration.
```

Once these steps are performed one can view the development/production server on the local host using http://local.rem.dbwebb.se/ where "rem.dbwebb.se" is the hostname configured in the Makefile.

When you change files you need to update the local installation.

```text
make local-publish   # Publish website to local host.
```



### Install on a production server using https

Perform the steps above to "[Install on a production server using http](#install-on-a-production-server-using-http)".




How to use and documentation
----------------------------------

The starting page contains the documentation on how to use it.

You can read the documentation on the [sample installation site](https://rem.dbwebb.se) or unstyled through this Git repo in [`content/index.md`](content/index.md).



```
 .  
..:  Copyright (c) 2017-2018 Mikael Roos (mos@dbwebb.se)
```