# Build from debian image
FROM debian:stable-slim
MAINTAINER Petri Kataja <peejkoo@gmail.com>

# Install packages
RUN apt-get update
RUN apt-get install -y git libapache2-mod-php curl apache2 php php-gd php-curl mariadb-server mariadb-client php-json php-mysql php-readline php-zip php-xml php-intl php-bz2 php-gmp php composer nodejs wget npm  vim  zip unzip  php-mbstring php-gettext openssh-server

# Enable apache / php modules
RUN a2enmod rewrite
RUN a2enmod ssl
RUN phpenmod mbstring

# Add dev user so we can login with ssh
RUN useradd dev
RUN echo "dev:Qwerty12345" | chpasswd
RUN usermod --shell /bin/bash dev
RUN usermod -G www-data dev

# Install phpmyadmin
RUN wget https://files.phpmyadmin.net/phpMyAdmin/5.0.0/phpMyAdmin-5.0.0-all-languages.zip
RUN unzip phpMyAdmin-5.0.0-all-languages.zip && rm phpMyAdmin-5.0.0-all-languages.zip
RUN mv phpMyAdmin-5.0.0-all-languages /usr/share/phpmyadmin
COPY phpmyadmin.conf /etc/apache2/conf-available/phpmyadmin.conf
RUN a2enconf phpmyadmin.conf
RUN mkdir -p /var/lib/phpmyadmin/tmp
RUN chown www-data:www-data /var/lib/phpmyadmin/tmp

# Create phpmyadmin db
RUN service mysql start; mysql -h localhost -u root -e "CREATE DATABASE phpmyadmin DEFAULT CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"; mysql -h localhost -u root -e "GRANT ALL ON *.* TO 'dev'@'%' IDENTIFIED BY 'Qwerty12345';"

# Expose basic ports
EXPOSE 22 80 443 3306

# Export volumes
VOLUME  ["/var/www/html/", "/var/log/apache2/" ]

COPY init.sh .
RUN chmod o+x init.sh
CMD ["./init.sh"]


