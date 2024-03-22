FROM nginx:alpine

ENV BIND_PORT=80
ENV REMOTE_HOST=google.com
ENV REMOTE_PORT=80

COPY nginx.conf.template /etc/nginx/

CMD ["/bin/sh", "-c", "envsubst < /etc/nginx/nginx.conf.template > /etc/nginx/nginx.conf && exec nginx -g 'daemon off;'"]
