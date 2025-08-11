# mbentley/debian

These are docker images based off of official Debian images on Docker Hub.

## Why

The images on Docker Hub are not always updated as regularly as I would like.  They can ship vulnerable libraries/binaries so in order to combat that, I am maintaining my own rebased images.  There are no customizations outside of patching and rebasing the images.

## Tags

The following is a list of multi-arch (`amd64`, `arm64`, `armv7`) tags for each release.

* __Hint__: You can also use the same rebased image tag with `-<arch>` appended (e.g. - `mbentley/debian:latest-amd64`)

| Distro | Base Image | Rebased Image |
| ------ | ---------- | ------------- |
| Debian | `debian:sid` | `mbentley/debian:sid` |
| Debian | `debian:latest`<br>`debian:trixie` | `mbentley/debian:latest`<br>`mbentley/debian:trixie` |
| Debian | `debian:bookworm` | `mbentley/debian:bookworm` |
| Debian | `debian:bullseye` | `mbentley/debian:bullseye` |
| Debian | `debian/eol:buster` | `mbentley/debian:buster` |
| Debian | `debian/eol:stretch` | `mbentley/debian:stretch` |
| Debian | `debian/eol:jessie` | `mbentley/debian:jessie` |

## Re-Building the Images

### Debian

``` bash
for VERSION in sid trixie bookworm bullseye buster
do
  docker build --pull --build-arg IMAGE_TAG="${VERSION}" -t "mbentley/debian:${VERSION}" -f Dockerfile .
done
```

``` bash
for VERSION in buster stretch jessie
do
  docker build --pull --build-arg IMAGE_TAG="${VERSION}" -t "mbentley/debian:${VERSION}" -f Dockerfile.eol .
done
```
