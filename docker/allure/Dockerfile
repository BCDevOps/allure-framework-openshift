FROM frankescobar/allure-docker-service:2.13.6

USER root

# The root group needs access the directories under /app for the
# container to function in OpenShift.
RUN chown -R allure:root /app \
    && chmod -R ug+rw /app

USER allure
