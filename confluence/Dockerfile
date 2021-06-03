FROM atlassian/confluence-server:7-adoptopenjdk11

COPY agent/atlassian-agent-v1.2.3.jar /opt/atlassian/confluence/atlassian-agent.jar

RUN echo 'export CATALINA_OPTS="-javaagent:/opt/atlassian/confluence/atlassian-agent.jar ${CATALINA_OPTS}"' \
    >> /opt/atlassian/confluence/bin/setenv.sh