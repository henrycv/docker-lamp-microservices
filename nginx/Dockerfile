FROM nginx

MAINTAINER Yevhenii Dumskyi "yevhenii.dumskyi@gmail.com"

RUN rm -fR /etc/nginx/conf.d/*
RUN rm -fR /etc/nginx/sites-enabled/*

COPY ./nginx.conf /etc/nginx/nginx.conf
COPY sites/* /etc/nginx/sites-enabled/
