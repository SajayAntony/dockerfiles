FROM microsoft/azure-cli:latest

ENV VERSION v2.9.0

MAINTAINER  Sajay Antony <sajaya@microsoft.com>

# Enable SSL
RUN apk --update add ca-certificates wget python curl tar

# Install Kubectl
RUN az aks install-cli 

# Install Helm
ENV FILENAME helm-${VERSION}-linux-amd64.tar.gz
ENV HELM_URL https://storage.googleapis.com/kubernetes-helm/${FILENAME}

RUN curl -o /tmp/$FILENAME ${HELM_URL} \
  && tar -zxvf /tmp/${FILENAME} -C /tmp \
  && mv /tmp/linux-amd64/helm /bin/helm \
  && rm -rf /tmp

# Run as non-root
# Mount azure credentials onto  /home/appuser/.azure/accessTokens.json
RUN addgroup -g 1000 -S appgroup  && \
    adduser -u 1000 -S  appuser -G appgroup

USER appuser

