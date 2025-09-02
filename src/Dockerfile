# Latest version from stable based on Debian bookworm-slim
FROM nginx:mainline

# Remove the default static site that ships with the image
RUN rm -rf /usr/share/nginx/html/*

# Copy our local html folder into the location Nginx expects
COPY html/ /usr/share/nginx/html/

# Expose the default HTTP port (optional – Docker does it automatically)
EXPOSE 80

# No CMD needed – the base image already starts nginx in foreground
