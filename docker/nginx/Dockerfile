FROM amazonlinux:2

RUN yum -y update

RUN amazon-linux-extras install nginx1

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]

COPY ./default.conf /etc/nginx/conf.d/default.conf
COPY ./nginx.conf /etc/nginx/nginx.conf