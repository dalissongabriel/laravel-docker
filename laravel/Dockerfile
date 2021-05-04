FROM php:8.0.3-cli-alpine3.13 AS builder
WORKDIR /workspace
RUN apk update && \
    apk add bash 
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
    php composer-setup.php --install-dir=/usr/local/bin --filename=composer && \
    php -r "unlink('composer-setup.php');"
RUN composer create-project laravel/laravel laravel
ENTRYPOINT [ "php", "laravel/artisan", "serve" ]
CMD [ "--host","0.0.0.0" ]


FROM php:8.0.3-fpm-alpine3.13
WORKDIR /workspace
COPY --from=builder /workspace/laravel ./laravel
RUN chown -R www-data:www-data /workspace
RUN ln -s /workspace/laravel/public/index.php /index.php
EXPOSE 9000
CMD ["php-fpm"]