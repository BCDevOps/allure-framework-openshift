FROM frankescobar/allure-docker-service-ui:7.0.0

USER root

# The root group needs access the directories under /app for the
# container to function in OpenShift.
RUN chown -R node:root /app \
    && chmod -R ug+rw /app

USER node
