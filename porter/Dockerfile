FROM alpine:3.10
RUN apk add curl --no-cache
RUN  sh -c 'curl https://cdn.deislabs.io/porter/latest/install-linux.sh | sh'
ENTRYPOINT ["/root/.porter/porter"]
