FROM fluent/fluentd:v1.12.0-debian-1.0
USER root
RUN apt-get add curl
RUN gem uninstall -I elasticsearch && gem install elasticsearch -v 7.17.0
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-document", "--version", "5.0.3"]
USER fluent

# # image based on fluentd v1.14-1
# FROM fluentd:v1.14-1

# # Use root account to use apk
# USER root

# # below RUN includes plugin as examples elasticsearch is not required# you may customize including plugins as you wish
# RUN apk add --no-cache --update --virtual .build-deps \
#         sudo build-base ruby-dev \
# && gem uninstall -I elasticsearch \
# && gem install elasticsearch -v 8.2.0 \
# && sudo gem install fluent-plugin-elasticsearch -v 5.2.1 \
# && sudo gem sources --clear-all \
# && apk del .build-deps \
# && rm -rf /tmp/* /var/tmp/* /usr/lib/ruby/gems/*/cache/*.gem

# # copy fluentd configuration from host image
# COPY ./conf/fluent.conf /fluentd/etc/
# # copy binary start file
# COPY entrypoint.sh /bin/

# RUN chmod +x /bin/entrypoint.sh

# USER fluent