FROM centos:centos7
# Dockerfile for running a httpd that contains the necessary modules to run
# a wordpress site. The wordpress itself is not included: you better store
# the wordpress files with your custom plugins and themes seperately in a 
# version control system, for example with git:
# https://davidwinter.me/install-and-manage-wordpress-with-git/

# Sendmail is not working. Use a plugin like wp-mail-smtp to send emails 
# from wordpress: https://wordpress.org/plugins/wp-mail-smtp/

LABEL Name "Apache with all necessary PHP modules to run a wordpress site"
LABEL Version 0.0.1
LABEL Maintainer "Dries Verachtert" <dries.verachtert@dries.eu>

RUN yum install -y epel-release && \
	yum install -y php php-mysqli php-filter php-ctype php-simplepie \
		php-getid3 php-curl php-date php-dom php-exif \
		php-fileinfo php-ftp php-gd php-gettext php-hash php-conv \
		php-json php-libxml php-mbstring php-openssl php-pcre \
		php-posix php-simplexml php-sockets php-spl \
		php-tokenizer php-xml php-zip php-zlib httpd fontconfig && \
	yum clean all && \
	sed -i '131,158s/AllowOverride None/AllowOverride All/g;' /etc/httpd/conf/httpd.conf \
	echo ServerTokens Prod >> /etc/httpd/conf/httpd.conf
# Previous command: make sure the .htaccess of a wordpress site is working.
# The sed command should only change the AllowOverride in the /var/www/html
# section with that range of linenumbers.

# Only needed if you want to use cli tools in this container to access mariadb:
RUN yum install -y mariadb
# Only needed if you want to run phantomjs from scripts:
RUN yum install -y fontconfig

EXPOSE 80
VOLUME /var/www

CMD /usr/sbin/httpd -D FOREGROUND
