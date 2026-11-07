FROM alpine:3.24

RUN apk add --no-cache \
    bash \
	curl \
	ca-certificates \
	libc6-compat \
	coreutils \
	findutils \
	tree

ENV PATH="/root/.local/bin:${PATH}"
WORKDIR /app

RUN wget -qO- https://github.com/block/goose/releases/download/stable/download_cli.sh | CONFIGURE=false bash

RUN wget -O /tmp/ttyd.x86_64 https://github.com/tsl0922/ttyd/releases/download/1.7.7/ttyd.x86_64
RUN chmod +x /tmp/ttyd.x86_64
RUN mv /tmp/ttyd.x86_64 /usr/local/bin/ttyd

# Expose port for ttyd
EXPOSE 7681

# Set entrypoint to ttyd running goose session
ENTRYPOINT ["ttyd", "-W"]
CMD ["goose"]
