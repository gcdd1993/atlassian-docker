FROM atlassian/jira-software:8.16

COPY agent/atlassian-agent-v1.2.3.jar /opt/atlassian/jira/atlassian-agent.jar

RUN echo 'export CATALINA_OPTS="-javaagent:/opt/atlassian/jira/atlassian-agent.jar ${CATALINA_OPTS}"' \
    >> /opt/atlassian/jira/bin/setenv.sh