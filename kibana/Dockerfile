FROM docker.elastic.co/kibana/kibana:8.3.0

# Set environment variables
ENV ELASTICSEARCH_HOSTS=http://your-elasticsearch-url:9200
ENV ELASTICSEARCH_USERNAME=your-username
ENV ELASTICSEARCH_PASSWORD=your-password

# Copy configuration
#COPY kibana.yml /usr/share/kibana/config/kibana.yml

# Set a non-root user
USER kibana

# Expose the port Kibana runs on
EXPOSE 5601

# Healthcheck to ensure service is running
HEALTHCHECK --interval=10s --timeout=5s --retries=3 \
  CMD curl -f http://localhost:5601/api/status || exit 1

# Run Kibana process on container start. This is already the default CMD in the base image,
# but reiterated here for clarity. No need to run as a background process, Docker handles that.
CMD ["/usr/share/kibana/bin/kibana"]