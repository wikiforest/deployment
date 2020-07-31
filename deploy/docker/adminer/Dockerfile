FROM adminer:fastcgi

WORKDIR /var/www/html

RUN wget https://jqueryui.com/resources/download/jquery-ui-1.12.1.zip && unzip jquery-ui-1.12.1.zip \
    && mv jquery-ui-1.12.1 jquery-ui \
    && rm jquery-ui-1.12.1.zip
