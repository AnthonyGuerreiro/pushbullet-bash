FROM alpine/git as BUILD

ARG PB_VERSION=1
ENV PB_VERSION=${PB_VERSION}

RUN git clone --branch ${PB_VERSION} https://github.com/AnthonyGuerreiro/pushbullet-bash.git /.pb/ 2>/dev/null && \ 
    cd /.pb/ && \
    git submodule init && \
    git submodule update


FROM alpine:3.8

COPY --from=BUILD /.pb/ /.pb/
ADD entrypoint /entrypoint

RUN apk add --no-cache jq curl && \
    sed -i "5s/2/19/" /etc/crontabs/root && \
\
    echo "/.pb/pushbullet push all note \"\$1\" \"\$2\"" > /usr/bin/push && \
    chmod +x /usr/bin/push && \
\
    chmod +x /entrypoint
ENTRYPOINT ["/entrypoint"]
