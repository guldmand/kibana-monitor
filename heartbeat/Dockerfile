# Use the official Heartbeat Docker image from Elastic
FROM docker.elastic.co/beats/heartbeat:7.10.0

# Copy your Heartbeat configuration file into the container
COPY heartbeat.yml /usr/share/heartbeat/heartbeat.yml

# Ensure correct file permissions and run as non-root user for security
USER root
RUN chown heartbeat:heartbeat /usr/share/heartbeat/heartbeat.yml
USER heartbeat

# Set the container to run Heartbeat when it starts
ENTRYPOINT ["/usr/share/heartbeat/heartbeat"]
CMD ["-e", "-c", "/usr/share/heartbeat/heartbeat.yml"]
