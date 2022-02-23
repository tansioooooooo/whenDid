FROM amazonlinux:2

RUN yum -y update

RUN yum install -y procps net-tools less glibc-lanpack-ja make

# install php8
RUN amazon-linux-extras install php8.0 -y
RUN yum -y install php-devel php-mbstring php-gd php-xml php-pear

# Composer install
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
RUN php composer-setup.php --version=2.2.6
RUN php -r "unlink('composer-setup.php');"
RUN mv composer.phar /usr/local/bin/composer

# use php-fpm default tcp
EXPOSE 9000

# run php-fpm in the foreground
ENTRYPOINT /usr/sbin/php-fpm -F

COPY ./www.conf /etc/php-fpm.d/www.conf
COPY ./php.ini /usr/local/etc/php/php.ini