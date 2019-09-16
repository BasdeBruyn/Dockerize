FROM nginx:latest

WORKDIR /usr/share/nginx/html

COPY Angular/dist/frontend/* ./

WORKDIR /etc/nginx/conf.d

COPY config.conf .

RUN rm default.conf