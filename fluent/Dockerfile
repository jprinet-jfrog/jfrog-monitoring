FROM fluent/fluentd:v1.11-debian-1
LABEL maintainer="Jérôme Prinet" 

ARG FLUENT_CONFIG_FILE

# use in fluent configuration file as jfrog tool installation folder
ENV JFROG_HOME ""

# copy fluent configuration file
ADD ${FLUENT_CONFIG_FILE} /fluentd/etc/fluent.conf

# install prometheus plugin as root
USER root
RUN gem install fluent-plugin-prometheus
USER fluent
