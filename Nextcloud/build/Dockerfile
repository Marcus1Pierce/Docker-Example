FROM nextcloud:29-fpm

RUN apt update && \
      apt install -y procps smbclient libsmbclient-dev libmagickcore-6.q16-6-extra unrar-free p7zip p7zip-full \
      nano cron curl ghostscript libldap2-dev iputils-ping && \
      # Not supported yet python3-pip
      apt autoclean && \
      rm -rf /var/lib/apt/lists/*
      # Because python3-pip not support, pip3 install youtube-dl can't execute command

# Samba client php extension
RUN pecl install smbclient
RUN docker-php-ext-enable smbclient

# Install php-ldap Extension
RUN docker-php-ext-install ldap

# inotify extension
RUN pecl install inotify

# For LibreSign preview image
RUN sed -i'' 's|.*<policy domain="coder".*"PDF".*|<policy domain="coder" rights="read \| write" pattern="PDF" />|g' /etc/ImageMagick-6/policy.xml
