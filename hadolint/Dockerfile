FROM alpine:3.13.5

ENV HADOLINT_VERSION=2.1.0
ENV HADOLINT_SHA256SUM=ecaf24a8d9dec2f5e16a8f951a6de51bfa9e43f285f4c751b208a9d90c66a0ce
ENV HADOLINT_DOWNLOAD=https://github.com/hadolint/hadolint/releases/download/v${HADOLINT_VERSION}/hadolint-Linux-x86_64

COPY hadolint-action.sh /usr/local/bin/hadolint-action

COPY entrypoint.sh /entrypoint.sh
COPY hadolint.json /hadolint.json

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