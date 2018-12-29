# docker-clear
Bash script to stop all Docker services and remove unused data

## Summary

When developing with Docker you will likely accumulate a large number of unused images.  These can consume a significant amount of space (have a look using `docker system df`).  This can be a particular issue when running Docker in a virtual environment where disk space is limited.

From time to time you may want to clean up your Docker development environment.  This script stops all Docker services, stacks and containers, leaves the swarm (if applicable) and removes unused data, so please **ensure you don't have important data in your containers before using the script!**

All containers, networks, images and build caches are removed.  Volumes are retained but can be removed by passing "--volumes" to the script as an argument.  Dangling images (those without a tag) can be removed by passing "--all".  See https://docs.docker.com/engine/reference/commandline/system_prune/ for more information.

:exclamation: **Use with Docker 17.06.1 or higher.  The script will remove all volumes without warning for earlier versions.  Use at own risk!**

## Instructions for use

* Download and save in your home directory
* Run using `~/docker-clear`
* Pass `--volumes` to the script to remove all volumes
* Pass `--all` to the script to remove *all* images and not just dangling images

## Using Docker as a non-root user

The script calls `docker` rather than `sudo docker`.  The following commands add the current user to a `docker` Unix group.  Members of this group can run Docker commands without using `sudo`.  See https://docs.docker.com/install/linux/linux-postinstall/#manage-docker-as-a-non-root-user for more information and security implications.

```
$ sudo groupadd docker
$ sudo usermod -aG docker $USER
```

Log out and back in after running the above.

## Acknowledgements

Based on an idea and initial script from Dale Whinham (https://dope.fish and https://github.com/dwhinham).

## Licence

Made available under the MIT license https://github.com/philipdarke/docker-clear/blob/master/LICENSE.
