
ARG PHP_VERSION
FROM bref/build-php-$PHP_VERSION:1.7.4 AS ext

RUN pecl install openswoole-4.12.0
RUN cp `php-config --extension-dir`/openswoole.so /tmp/openswoole.so
RUN echo 'extension=/opt/bref-extra/openswoole.so' > /tmp/ext.ini

FROM scratch

COPY --from=ext /tmp/openswoole.so /opt/bref-extra/openswoole.so
COPY --from=ext /tmp/ext.ini /opt/bref/etc/php/conf.d/ext-openswoole.ini
