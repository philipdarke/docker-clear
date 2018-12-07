# docker-clear
Bash script to stop all Docker services and remove unused data

## Summary

The script stops all Docker services, stacks and containers, removes unused data and takes down the node from a swarm. Volumes are retained but can be removed by passing "--volumes" to the script as an argument.

**Use with Docker 17.06.1 or higher.  Script will remove all volumes for earlier versions.  Use at own risk!**

## Instructions for use

* Download and save in your home directory
* Run using `~/docker-clear`
* Pass `--volumes` to the script to remove all volumes
* Pass `--all` to the script to remove *all* images and not just dangling images

## Acknowledgements

Based on an idea and initial script from https://github.com/dwhinham

## Licence

Made available under the MIT license https://github.com/philipdarke/docker-clear/blob/master/LICENSE
