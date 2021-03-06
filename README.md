
# docker-electrumx

[![Build Status](https://travis-ci.org/lukechilds/docker-electrumx.svg?branch=master)](https://travis-ci.org/lukechilds/docker-electrumx)
[![Image Layers](https://images.microbadger.com/badges/image/lukechilds/electrumx.svg)](https://microbadger.com/images/lukechilds/electrumx)
[![Docker Pulls](https://img.shields.io/docker/pulls/lukechilds/electrumx.svg)](https://hub.docker.com/r/lukechilds/electrumx/)

> Run an Electrum server with one command

An easily configurable Docker image for running an Electrum server.

## Usage
**Installation** 

Build the image with `docker build -t andgohq/electrumx .`

**Running the instance**

Since the block generation is 20 seconds, the ElectrumX server database flush count is running full after ~14 days. 
In order to tackle this, it is necessary to remove the electrumx database folder and let it re-build on the next ElectrumX startup.

To run the instance, use the provided docker-compose files in [Marunouchi-Infra](https://github.com/andgohq/marunouchi-infra) and `docker-compose up -d`


If there's an SSL certificate/key (`electrumx.crt`/`electrumx.key`) in the `/data` volume it'll be used. If not, one will be generated for you.

You can view all ElectrumX environment variables here: https://github.com/kyuupichan/electrumx/blob/master/docs/environment.rst

### TCP Port

By default only the SSL port is exposed. You can expose the unencrypted TCP port with `-p 50001:50001`, although this is strongly discouraged.

### Version

You can also run a specific version of ElectrumX if you want.

```
docker run \
  -v /home/username/electrumx:/data \
  -e DAEMON_URL=http://user:pass@host:port \
  -e COIN=Bitcoin \
  -p 50002:50002 \
  lukechilds/electrumx:v1.2.1
```

## License

MIT © Luke Childs
