FROM node:22

# Install ghost-cli
RUN npm install -g ghost-cli@latest

# Create non-root user
RUN useradd --create-home --shell /bin/bash ghostuser

# Use the non-root user
USER ghostuser

# Set the working directory
WORKDIR /home/ghostuser/ghost-local

# Install Ghost and configure to bind to 0.0.0.0
RUN ghost install local --no-setup-nginx --no-setup-systemd --no-start && \
    ghost config set server.host 0.0.0.0

# Expose the port Ghost listens on
EXPOSE 2368

# Start Ghost in foreground (container lifecycle is tied to the process)
CMD ["ghost", "run"]

#########################################
# docker build -t ghost-local .
# docker run -it -p 2368:2368 ghost-local
#########################################
