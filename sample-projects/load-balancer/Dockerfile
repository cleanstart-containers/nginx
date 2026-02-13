# Dockerfile for Nginx Load Balancer
FROM cleanstart/nginx:latest-dev

USER root

# Copy custom nginx configuration
COPY nginx.conf /etc/nginx/nginx.conf

# Copy frontend static files
COPY frontend/index.html /usr/share/nginx/html/

# Create pid directory (base image dirs are protected, so we only add what's missing)
RUN mkdir -p /run/nginx

# Expose port 80
EXPOSE 80

# Start nginx (base image may set ENTRYPOINT ["nginx"], so avoid doubling the command)
ENTRYPOINT []
CMD ["nginx", "-g", "daemon off;"]
