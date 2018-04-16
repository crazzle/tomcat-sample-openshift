FROM jboss/wildfly

USER root:root
RUN chmod -R 777 /opt/jboss/wildfly/standalone/
USER wildfly

COPY maven/ /opt/jboss/wildfly/standalone/deployments/
