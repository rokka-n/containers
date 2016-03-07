# Working with ember from docker container 

Develop ember apps from a container. Nothing is required to be installed locally, except docker.

## Installation

* `git clone git@github.com:rokka-n/containers.git` this repo
* cd into the `docker_ember_cli`

You may either build container from Docker file or allow docker-compose to pull it from hub

Initiate new project:
* `docker-compose run --rm ember init`

Notice that .ember_cli contains option for liveReloadBaseHost

Add hostname from liveReloadBaseHost to /etc/hosts file, with resolution to docker-machine ip

Run as sudo:
* `echo "\`docker-machine ip\` ember" >> /etc/hosts"`

## Running / Development

* `docker-compose run --rm -p 4200:4200 -p 35729:35729 ember server --live-reload-port 35729`
* Visit your app at [http://docker-machine ip:4200](http://docker-machine ip:4200).

### Code Generators

Make use of the many generators for code, try `docker-compose run --rm ember help generate` for more details

### Running Tests

* `docker-compose run --rm ember test`
* `docker-compose run --rm ember test --server`

### Building

* `docker-compose run --rm ember build` (development)
* `docker-compose run --rm ember build --environment production` (production)

## Other tools
You can run npm, bower, phantomjs or add your own commands, please see docker-compose.yml
* `docker-compose run --rm node'`

You may add alias to .bashrc to make above commands short and sweet
* `alias node='docker-compose -f ~/ember/docker_ember_cli/docker-compose.yml run --rm npm'`
