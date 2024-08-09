# Docker image base to use
FROM ubuntu

# Additional data for the image, in this case its a maintainer
LABEL maintainer="Carlos Nunez <dev@carlosnunez.me>"

# Specify which user to use for any Docker commands underneath it
# Better practice is to use a non-root user
USER root

# Copy file from a directory provided to the container image
# Directory provided in Docker build is called the context
# The context is usually the working directory but can be changed
COPY ./entrypoint.bash /

# Run statement are commands to run when the container is built
# Appropriately to install additional software or config file needed for the application
RUN apt -y update
RUN apt -y install curl bash
RUN chmod 755 /entrypoint.bash

USER nobody

# The entry point tell Docker what command to run when the container is started
# CMD command can be used as well
ENTRYPOINT [ "/entrypoint.bash" ]
