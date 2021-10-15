FROM alpine:3.14.2

ENV HADOLINT_VERSION=2.7.0
ENV HADOLINT_SHA256SUM=cdd5ca6f07f72053e8f2d18a9390a7b7fc6e819b6a251835971411f300dab8e6
ENV HADOLINT_DOWNLOAD=https://github.com/hadolint/hadolint/releases/download/v${HADOLINT_VERSION}/hadolint-Linux-x86_64

COPY hadolint-action.sh /usr/local/bin/hadolint-action

SHELL ["/bin/ash", "-eo", "pipefail", "-c"]
# hadolint ignore=DL3018
RUN apk add --no-cache \
    bash \
    ca-certificates \
    coreutils \
    curl \
    jq &&\
    curl -o /usr/bin/hadolint -fsSL "${HADOLINT_DOWNLOAD}" &&\
    echo "${HADOLINT_SHA256SUM}  /usr/bin/hadolint" | sha256sum -c - &&\
    chmod +x /usr/bin/hadolint /usr/local/bin/hadolint-action


CMD ["hadolint-action"]