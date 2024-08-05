# syntax=docker/dockerfile:1
ARG VERSION=1.25

# choose a light weight base image
FROM nginx:${VERSION}-alpine-slim AS base

LABEL Maintainer="Joseph Haddison" \
      Email="joelhaddy07@gmail.com" \
      Team="SRE"

# create a sam user with UID 1234 GID 1234
# RUN addgroup -g 1000 devgroup && \
#    adduser -m -u 1000 -g devgroup dev

# USER dev    

ENV WORK_DIR=/usr/share/nginx/html

# working directory
WORKDIR ${WORK_DIR}

# copy all necessary web contents with a single command
COPY . ${WORK_DIR}

# expose static web site on a defined port
EXPOSE 80

# Add a health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=5s --retries=3 CMD curl -f http://localhost/ || exit 1

CMD ["nginx","-g","daemon off;"]