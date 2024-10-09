ARG APACHE_VERSION=""
FROM httpd:${APACHE_VERSION:+${APACHE_VERSION}-}alpine

# Instalar utilidades de Apache
RUN apk update && apk upgrade && \
    apk add --no-cache apache2-utils nano

RUN rm -rf /usr/local/apache2/conf/000-default.conf

# Copiar el archivo de configuración del virtual host
COPY museo.conf /usr/local/apache2/conf/museo.conf

# Incluir el archivo de configuración del virtual host

RUN echo "Include /usr/local/apache2/conf/museo.conf" >> /usr/local/apache2/conf/httpd.conf

# Asegurarse de que el contenedor ejecute Apache en primer plano
CMD ["httpd-foreground"]
