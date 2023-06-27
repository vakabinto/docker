FROM Ubuntu:latest AS BUILD-SITE
LABEL "author"="victor"
RUN apt update && apt install unzip -y
RUN mkdir moso
RUN cd moso && wget https://www.tooplate.com/zip-templates/2133_moso_interior.zip
RUN unzip 2133_moso_interior.zip && rm -rf 2133_moso_interior.zip
RUN cd 2133_moso_interior && tar czvf moso.tar.gz * && mv tar czvf moso.tar.gz ../ && rm -rf 2133_moso_interior

FROM Ubuntu:latest
RUN apt update && apt install apache2 && apt install git -y
CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
EXPOSE 80
WORKDIR /var/www/html
VOLUME /var/log/apache2
ADD --from=BUILD-SITE /moso/moso.tar.gz /var/www/html
