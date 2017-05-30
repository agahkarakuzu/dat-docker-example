# dat-docker-example

Example of serving an archive via HTTP and Dat on any service that supports Dockerfiles.

## Demo

This project serves a single Dat archive over HTTP and Dat using a docker container on [now.sh](https://now.sh).

Visit via HTTPS: https://dat-docker-example-gmqmkxczjt.now.sh

Visit with Dat protocol via [Beaker](https://beakerbrowser.com): [dat://5f7960b25fb8a2ad401e32dec525bf08a73113e7d27eabbf61140605286405b2/](dat://5f7960b25fb8a2ad401e32dec525bf08a73113e7d27eabbf61140605286405b2/)

Download with the Dat command-line tool: `dat clone 5f7960b25fb8a2ad401e32dec525bf08a73113e7d27eabbf61140605286405b2`


## What is this?

It's an attempt at hosting Dat archives on arbitrary services using docker that can be served via the Dat protocol and HTTP.

So far I've only tried pushing it to zeit's service [now.sh](https://now.sh).

There seems to be a few bugs to work out with the implementation that runs inside the docker container.

If I add files it doesn't always seem to download them properly.

If I delete content from a file sometimes it doesn't always delete properly until I add new text to replace it.

This behavior doesn't seem to exist when viewing the archive via Beaker & `dat://`.

## Run the example

### Run locally

#### First steps

- `git clone` this repo
- `cd dat-docker-example`

#### Without docker

To run the example without docker:

- `npm install`
- `npm start`

#### With docker

Make sure you have [docker installed](https://www.docker.com/products/overview#/install_the_platform) on your system.

- `docker build -t dat-docker-example .`
- `docker run -p 3000:3000 -p 3282:3282 -d dat-docker-example`

## Deploy

### Deploy with `now`

- `npm install -g now`
- `now --docker`
