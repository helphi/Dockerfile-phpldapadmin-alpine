FROM alpine:3.6

RUN apk --no-cache add php5-apache2 phpldapadmin=1.2.3-r4

RUN mkdir -p /run/apache2 &&\
    rm -rf /var/www/localhost/htdocs &&\
    ln -sf /usr/share/webapps/phpldapadmin/htdocs/ /var/www/localhost/ &&\
    cp /etc/phpldapadmin/config.php.example /etc/phpldapadmin/config.php &&\
    sed -i 's#AllowOverride none#AllowOverride All#' /etc/apache2/httpd.conf &&\
    sed -i "s/^\/\/ \(\$servers->setValue('server','host','\).*\(');\)$/\1$SERVER_HOST\2/g" /etc/phpldapadmin/config.php &&\
    sed -i "s/^\/\/ \(\$servers->setValue('server','port',\).*\();\)$/\1$SERVER_PORT\2/g" /etc/phpldapadmin/config.php &&\
    sed -i "s/^\/\/ \(\$servers->setValue('server','tls',\).*\();\)$/\1$SERVER_TLS\2/g" /etc/phpldapadmin/config.php

EXPOSE 80

CMD ["httpd","-D","FOREGROUND"]
