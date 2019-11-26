FROM node:latest

# Set evironment variables
ENV APP_DIR=/app APP_PORT=3000

# Set db config
ENV DB_HOST=localhost DB_PORT=3306 DB_USER=root DB_PASSWORD=changeit

# From directory
WORKDIR ${APP_DIR}

# Copy files
ADD main.js .
ADD package.json .
ADD config config
ADD public public
ADD views views

# Install dependencies
RUN npm install

# App port
EXPOSE ${APP_PORT}

# Add healthcheck
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# Run app
ENTRYPOINT [ "node", "main.js" ]