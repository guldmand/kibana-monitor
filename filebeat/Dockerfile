# Use the official Filebeat image
FROM docker.elastic.co/beats/filebeat:7.10.0

# Copy your custom Filebeat configuration file
COPY filebeat.yml /usr/share/filebeat/filebeat.yml

# Set the correct file permissions
USER root
RUN chown root:filebeat /usr/share/filebeat/filebeat.yml
USER filebeat

# Set the container to use the filebeat command
CMD ["filebeat", "-e"]