# nginx/Dockerfile
FROM ubuntu:18.04

RUN rm -rf /etc/nginx/sites-enabled/default

COPY nginx.conf /etc/nginx/nginx.conf

COPY index.html /usr/share/nginx/html
COPY 404.html /usr/share/nginx/html

RUN  mkdir -p /etc/nginx/conf.d

RUN mkdir -p /etc/nginx/sites-available
RUN mkdir -p /etc/nginx/sites-enabled

COPY proxy.conf /etc/nginx/sites-available
RUN ln -s /etc/nginx/sites-available/proxy.conf /etc/nginx/sites-enabled/proxy.conf

COPY entrypoint.sh .
RUN chmod +x /entrypoint.sh

WORKDIR /etc/nginx 
#CMD nginx -g "daemon off;"
CMD /entrypoint.sh && nginx -g "daemon off;"
