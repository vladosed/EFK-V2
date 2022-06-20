FROM fluent/fluentd:v1.12.0-debian-1.0
USER root
RUN gem uninstall -I elasticsearch && gem install elasticsearch -v 7.4.2
RUN ["gem", "install", "fluent-plugin-elasticsearch", "--no-document", "--version", "5.0.3"]
RUN ["gem", "install", "fluent-plugin-secure-forward"]
RUN gem install elasticsearch-transport
USER fluent

