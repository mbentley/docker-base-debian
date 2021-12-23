# STAGE 0: use base image from Docker Hub and upgrade the existing packages
ARG IMAGE_TAG="${IMAGE_TAG:-3.15}"
FROM alpine:${IMAGE_TAG} AS base

RUN apk --no-cache upgrade --purge

# STAGE 1: copy contents of the original base image to a new image so we don't have overlapping files in layers
FROM scratch
COPY --from=base / /
LABEL maintainer="Matt Bentley <mbentley@mbentley.net>"
CMD ["/bin/sh"]
