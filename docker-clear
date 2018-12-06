#!/bin/sh
#
# Stops all Docker services, stacks and containers, removes unused data
# and takes down the node from a swarm.  Volumes are retained but can be
# removed by adding "--volumes" to line 32.
#
# IMPORTANT NOTE - use with Docker 17.06.1 or higher.  Script will remove all
# volumes for earlier versions.  Use at own risk!
#
# MIT LICENSE
#
# Copyright (c) 2018 Philip Darke philipdarke.com
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.

# Stop all running services
docker service rm $(docker service ls -q)

# Tear down all applications
docker stack rm $(docker stack ls --format "{{.Name}}")

# Stop any remaining running containers and remove all old containers
docker stop $(docker ps -a -q)

# Remove unused containers, networks and images (SEE IMPORTANT NOTE ABOVE)
docker system prune

# Remove node from the swarm (if in one)
docker swarm leave --force
