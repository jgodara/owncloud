![GitHub](https://img.shields.io/github/license/jgodara/owncloud.svg?style=flat-square)
![GitHub issues](https://img.shields.io/github/issues/jgodara/owncloud.svg)

# OwnCloud

A simple self-made and hosted cloud storage. This is for fun stuff, might deploy it later, idk.

This ships with an admin CLI to manage users and access keys.

## Installation

```shell
$ pipenv shell
$ pipenv install
```

Now, build the front-end

```
$ npm i
$ npm run build
```

### Installing Admin CLI

```shell
$ pipe install -e .
```

## Running

For this to work, you need to crate a folder `/owncloud` with appropriate read/write permissions on it.
It's recommended to mount a stoage media on this folder, but it should work without it.

After that, `python app.py` should be enough.

### Running with docker

Since I'm lazy at this time, you have to build the front-end first and then fire `docker-compose up`.

#### Running with docker on a Raspberry PI

`docker-compose` magic won't work here since Docker for ARM is different so we will need to change a few things around. First of those things would be to replace the `FROM python:3` tag in the `Dockerfile` with `FROM arm32v7/python:2.7.13-jessie`.

Then we will manually build and run the container.

```shell
$ docker build -t owncloud:stable .
$ docker run --name owncloud -p 8000:8000 -v /owncloud:/owncloud -d owncloud:stable
```
