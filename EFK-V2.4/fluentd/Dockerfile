FROM fluent/fluentd:v1.4-debian-onbuild
USER root

RUN ulimit -n 65536

RUN buildDeps="sudo make gcc g++ libc-dev ruby-dev" \
 && apt-get update \
 && apt-get install -y --no-install-recommends $buildDeps \
 && gem install \
        fluent-plugin-elasticsearch \
        fluent-plugin-record-reformer \
        fluent-plugin-systemd \
        fluent-plugin-kubernetes_metadata_filter \
        fluent-plugin-detect-exceptions \
        fluent-plugin-prometheus \
        fluent-plugin-record-modifier \
        fluent-plugin-forest \
        fluent-plugin-genhashvalue \
        fluent-plugin-elasticsearch-timestamp-check \
 && gem sources --clear-all \
 && SUDO_FORCE_REMOVE=yes \
    apt-get purge -y --auto-remove \
                  -o APT::AutoRemove::RecommendsImportant=false \
                  $buildDeps \
 && rm -rf /var/lib/apt/lists/* \
           /home/fluent/.gem/ruby/2.3.0/cache/*.gem \
 && mkdir /fluentd/etc/conf.d

COPY entrypoint.sh /bin/

RUN chmod +x /bin/entrypoint.sh