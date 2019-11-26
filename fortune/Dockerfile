FROM node:latest

### How the image is built ###
# Set environment variables
ENV APP_ROOT=/app
ENV APP_PORT=3000

# Create the directory and cd into it
WORKDIR ${APP_ROOT}

# Copy files into the image
ADD main.js .
ADD package.json .
ADD public public
ADD views views

# Install dependencies
RUN npm install

## How the image is provisioned ###
# Port which our container will be exposing
EXPOSE ${APP_PORT}

# Add healthcheck to the application
HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -f http://localhost:${APP_PORT}/health > /dev/null || exit 1

# Run the app
ENTRYPOINT [ "node", "main.js" ]
CMD [ "" ]
