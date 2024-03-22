FROM alpine:latest

ARG ARCH=amd64
ARG VERSION=0.56.0

WORKDIR /frp

RUN wget https://github.com/fatedier/frp/releases/download/v${VERSION}/frp_${VERSION}_linux_${ARCH}.tar.gz \
	&& tar xvfz frp_*.tar.gz -C /frp --strip-components=1 \
	&& rm -r ./frp_*.tar.gz \
	&& ln -s /frp/frps /usr/local/bin \
	&& ln -s /frp/frpc /usr/local/bin
