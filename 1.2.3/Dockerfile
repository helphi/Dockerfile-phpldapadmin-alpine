FROM alpine:3.6

RUN apk --no-cache add php5-apache2=5.6.31-r0 phpldapadmin=1.2.3-r4

RUN mkdir -p /run/apache2

EXPOSE 80

CMD ["httpd","-D","FOREGROUND"]
