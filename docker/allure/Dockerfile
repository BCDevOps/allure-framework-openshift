FROM frankescobar/allure-docker-service:2.17.2

USER root

# The root group needs access the directories under /app for the
# container to function in OpenShift.
RUN chown -R allure:root /app \
    && chmod -R ug+rw /app

# ===============================================================================================
# Additional mitigation for LOGBACK-1591
#   - Allure 2.17.2 uses Logabck 1.2.7
#       - https://github.com/allure-framework/allure2/compare/2.17.1...2.17.2#diff-c0dfa6bc7a8685217f70a860145fbdf416d449eaff052fa28352c5cec1a98c06R74
#   - Set logback.xml to read-only
#
# References:
#   - http://logback.qos.ch/news.html
#   - https://jira.qos.ch/browse/LOGBACK-1591
# -----------------------------------------------------------------------------------------------
RUN find / -name logback.xml -exec chmod ug-w {} \; 2>/dev/null
# ===============================================================================================

USER allure
