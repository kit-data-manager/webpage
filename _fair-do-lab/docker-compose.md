---
title: Local setup
breadcrumbs: /typed-pid-maker/local-setup
layout: default
description: Local setup using docker-compose.
repository_url: https://github.com/kit-data-manager/testbed4inf
repository_name: kit-data-manager/testbed4inf
navigation_id: fair_do_lab_index
---

[status]: status.html

# Local setup


A local instance of the FAIR DO Lab can be useful for developing applications, new services or simply to explore the Lab.
The default configuration is targets purposes.
It uses sandboxed (in-memory) PIDs, therefore no real publications happen, and everything is easy to reset.

The whole setup is based on docker-compose.

> **Please note that containers do by default not persist anything on your disk: If you remove the container, your data will be lost. Read the [server setup](server-setup.html) after reading this section, to learn how to persist the services state, like search index.**
> Among other actions, the following actions remove (or replace) containers and are therefore dangerous if you are not doing simple tests!
>
> * `docker compose down`
> * `docker container rm ...`

## Download

You will need to get the [repository content](https://github.com/kit-data-manager/testbed4inf.git) to set everything up. Either download and extract the content or use `git clone https://github.com/kit-data-manager/testbed4inf.git`.

## Docker-compose setup

Docker-Compose now comes with the default [docker installations](https://docs.docker.com/get-docker/) by default.
On the command line you can simply use it using `docker compose <command>` (no `-` required between `docker` and `compose`).

If you use a virtual-machine-based setup (e.g., because you use macOS), make sure to assign at least 4 GiB of RAM to your virtual machine (VM). You can do this the easiest using Docker Desktop in the preference menu under "Resources". The FAIR DO Lab consists of several services, and in sum the default of 2 GiB RAM will not be enough.

Using the `docker-compose.yml`, you can choose to exclude services not needed. For documentation about how the services depend on and relate to each other and about their stability, see the [status] page.

## Start the FAIR DO Lab

A single command will build and run the FAIR DO Lab: `docker compose up`. It will do the following steps:

* Build or download all required docker images. This step might take a while, as some services will be compiled in this process. After that, the [configuration] files will be copied from the repository folders into the services images. This implies that, if you want to change a [configuration] in the repository, you will need to re-build the services the changes will be applied. Alternatively, you can change the [configuration] within the container.

* Instantiate containers from those images, with the configuration given in `docker-compose.yml`.
* Run the containers.

Note that by default, persistence, for example the search index content, is bound to the container lifetime. Please see the warning at the top of this article.

## Updating the FAIR DO Lab

> Please see the warning at the top of the article if you to not want to loose your search index, sandboxed PIDs, or other data.

```bash
docker compose down  # dangerous! See text and warnings!
git pull  # or re-download the repository content
docker compose pull  # pull new images
docker compose up  # start Lab
```

## Removing the FAIR DO Lab

```bash
docker compose down
```

Then, remove the repository folder, for example using `rm -rf fair-do-lab` (if the repository folder is `fair-do-lab` in your case). What is then remaining is a set of images. If you use Docker Desktop, you can use the UI to delete the ones you do not require. Alternatively you can use `docker images` to list them and `docker rmi <image>` to delete an image.

## Further configuration

[configuration]: configuration.html

To change, for example, the PID system from sandboxed in-memory to a real handle prefix, please refer to the [configuration] section.