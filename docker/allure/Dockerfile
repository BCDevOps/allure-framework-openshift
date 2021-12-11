FROM frankescobar/allure-docker-service:2.13.8

USER root

# ===============================================================================================
# Mitigation for CVE-2021-44228
#
# References:
#   - https://logging.apache.org/log4j/2.x/security.html
# -----------------------------------------------------------------------------------------------
ENV LOG4J_FORMAT_MSG_NO_LOOKUPS=true
# ===============================================================================================

# The root group needs access the directories under /app for the
# container to function in OpenShift.
RUN chown -R allure:root /app \
    && chmod -R ug+rw /app

USER allure
