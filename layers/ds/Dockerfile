ARG PHP_VERSION
FROM bref/build-php-$PHP_VERSION:1.3.3 AS ext

RUN pecl install ds
RUN cp `php-config --extension-dir`/ds.so /tmp/ds.so
RUN echo 'extension=/opt/bref-extra/ds.so' > /tmp/ext.ini

# Build the final image with just the files we need
FROM scratch

# Copy things we installed to the final image
COPY --from=ext /tmp/ds.so /opt/bref-extra/ds.so
COPY --from=ext /tmp/ext.ini /opt/bref/etc/php/conf.d/ext-ds.ini
