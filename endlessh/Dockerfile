FROM alpine:latest

RUN apk add --no-cache --virtual=deps unzip build-base \
	&& wget https://github.com/skeeto/endlessh/archive/refs/heads/master.zip \
	&& unzip master.zip \
	&& rm -r ./master.zip \
	&& cd endlessh-master/ \
	&& make \
	&& mv $(pwd)/endlessh /usr/local/bin \
	&& cd .. \
	&& rm -r endlessh-master/ \
	&& apk del --purge deps

ENTRYPOINT ["endlessh"]
