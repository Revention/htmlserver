# Latest version from stable based on Debian bookworm-slim
FROM nginx:1.29.1-bookworm

# Label for maintainer
LABEL maintainer="25434575+Revention@users.noreply.github.com"
LABEL description="Statische HTML‑site voor development"

# Remove the default static site that ships with the image
RUN rm -rf /usr/share/nginx/html/*

# Copy our local html folder into the location Nginx expects
COPY --chown=nginx:nginx ../html/ /usr/share/nginx/html/

# Expose the default HTTP port (optional – Docker does it automatically)
EXPOSE 80

# No CMD needed – the base image already starts nginx in foreground
