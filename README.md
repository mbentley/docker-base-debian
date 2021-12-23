# Base Docker Images

These are docker images based off of official images on Docker Hub.

## Why

The images on Docker Hub are not always updated as regularly as I would like.  They can ship vulnerable libraries/binaries so in order to combat that, I am maintaining my own rebased images.  There are no customizations outside of patching and rebasing the images.

## Tags

The following is a list of multi-arch (`amd64`, `arm64`, `armv7`) tags for each release.
  * __Hint__: You can also use the same rebased image tag with `-<arch>` appended (e.g. - `mbentley/alpine:latest-amd64`)

| Distro | Base Image | Rebased Image |
| ------ | ---------- | ------------- |
| Alpine | `alpine:latest`<br>`alpine:3.15` | `mbentley/alpine:latest`<br>`mbentley/alpine:3.15` |
| Alpine | `alpine:3.14` | `mbentley/alpine:3.14` |
| Alpine | `alpine:3.13` | `mbentley/alpine:3.13` |
| Alpine | `alpine:3.12` | `mbentley/alpine:3.12` |
| Alpine | `alpine:3.11` | `mbentley/alpine:3.11` |
| Alpine | `alpine:3.10` | `mbentley/alpine:3.10` |
| Alpine | `alpine:3.9` | `mbentley/alpine:3.9` |
| | | |
| Debian | `debian:sid` | `mbentley/debian:sid` |
| Debian | `debian:latest`<br>`debian:bullseye` | `mbentley/debian:latest`<br>`mbentley/debian:bullseye` |
| Debian | `debian:buster` | `mbentley/debian:buster` |
| Debian | `debian:stretch` | `mbentley/debian:stretch` |
| Debian | `debian:jessie` | `mbentley/debian:jessie` |
| | | |
| Ubuntu | `ubuntu:latest`<br>`ubuntu:20.04` | `mbentley/ubuntu:latest`<br>`mbentley/ubuntu:20.04` |
| Ubuntu | `ubuntu:18.04` | `mbentley/ubuntu:18.04` |
| Ubuntu | `ubuntu:16.04` | `mbentley/ubuntu:16.04` |

## Re-Building the Images

### Alpine

``` bash
for VERSION in 3.15 3.14 3.13 3.12 3.11 3.10 3.9
do
  docker build --pull --build-arg IMAGE_TAG="${VERSION}" -t "mbentley/alpine:${VERSION}" -f Dockerfile.alpine .
done
```

### Debian

``` bash
for VERSION in sid bullseye buster stretch jessie
do
  docker build --pull --build-arg IMAGE_TAG="${VERSION}" -t "mbentley/debian:${VERSION}" -f Dockerfile.debian .
done
```

### Ubuntu

``` bash
for VERSION in 20.04 18.04 16.04
do
  docker build --pull --build-arg IMAGE_TAG="${VERSION}" -t "mbentley/ubuntu:${VERSION}" -f Dockerfile.ubuntu .
done
```
