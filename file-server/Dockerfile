FROM nginx:1.15-alpine

COPY nginx/default.conf /etc/nginx/conf.d/default.conf
COPY html/index.html /usr/share/nginx/html

RUN mkdir /usr/share/nginx/html/data
