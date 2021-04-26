FROM public.ecr.aws/w1x5y4f3/arm64v8/alpine:3.13.5
LABEL maintainer="Glen Stummer <glen@glen.dev>"
ENV TRIVY_VERSION=0.16.0
SHELL ["/bin/ash", "-eo", "pipefail", "-c"]

COPY entrypoint.sh /
RUN apk --no-cache add bash
RUN chmod +x /entrypoint.sh

# hadolint ignore=DL3018
RUN apk add --no-cache --virtual .build-deps \
    wget &&\
    wget --progress=dot:giga https://github.com/aquasecurity/trivy/releases/download/v${TRIVY_VERSION}/trivy_${TRIVY_VERSION}_Linux-ARM64.tar.gz &&\
    tar -xvzf  trivy_${TRIVY_VERSION}_Linux-ARM64.tar.gz &&\
    rm -rf trivy_${TRIVY_VERSION}_Linux-ARM64.tar.gz LICENSE README.md contrib &&\
    mv trivy /usr/local/bin/ &&\
    apk del --purge .build-deps

ENTRYPOINT ["/entrypoint.sh"]
