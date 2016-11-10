FROM nginx:1.11.5-alpine
MAINTAINER Ta Dat <ttdat1@gmail.com>

RUN rm -rf /etc/nginx/conf.d/default.conf
COPY conf/jenkins.conf /etc/nginx/conf.d/jenkins.conf
COPY conf/nginx.conf /etc/nginx/nginx.conf

EXPOSE 80

CMD ["nginx"]
