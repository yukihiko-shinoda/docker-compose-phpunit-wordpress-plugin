FROM php:7.2.24-apache-buster
# ↓ @see https://github.com/docker-library/php/issues/391#issuecomment-346590029
RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli
RUN apt update
RUN apt install -y wget
RUN sh -c 'wget https://raw.githubusercontent.com/composer/getcomposer.org/76a7060ccb93902cd7576b67264ad91c8a2700e2/web/installer -O - -q | php -- --quiet' \
 && mv ./composer.phar /bin/composer
# ↓ To install dependency of PHPUnit 5.* at least myclabs/deep-copy
RUN apt install -y git
# ↓ 2019-11-18 WordPress supports PHPUnit 5.x
# ↓ @see https://make.wordpress.org/cli/handbook/plugin-unit-tests/
RUN composer global require phpunit/phpunit:5.*
ENV PATH $PATH:/root/.composer/vendor/bin
# ↓ Dependencies for install-wp-tests.sh
RUN apt install -y subversion default-mysql-client
RUN wget -O /usr/bin/install-wp-tests https://raw.githubusercontent.com/wp-cli/scaffold-command/master/templates/install-wp-tests.sh \
 && chmod +x /usr/bin/install-wp-tests
ENV WP_CORE_DIR /usr/src/wordpress/
RUN touch wp-tests-config.php \
 && install-wp-tests '' '' '' localhost 4.3 true\
 && rm -f wp-tests-config.php \
 && rm -f /tmp/install-wp-tests.sh
# ↓ @see http://docs.docker.jp/compose/startup-order.html
RUN wget -O /usr/bin/wait-for-it https://raw.githubusercontent.com/vishnubob/wait-for-it/master/wait-for-it.sh \
 && chmod +x /usr/bin/wait-for-it
COPY ./entrypoint.sh /usr/bin/entrypoint
RUN chmod +x /usr/bin/entrypoint
WORKDIR /plugin
ENTRYPOINT ["entrypoint"]
CMD [ "phpunit" ]
