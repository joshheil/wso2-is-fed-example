FROM openjdk:8-jdk

# Download wso2 and setup paths
RUN wget https://s3.amazonaws.com/wso2-ent/wso2is-5.3.0.zip && \
    unzip wso2is-5.3.0.zip -d /opt && \
    mv /opt/wso2is-5.3.0 /opt/wso2 && \
    rm wso2is-5.3.0.zip

ENTRYPOINT ["/opt/wso2/bin/wso2server.sh"]