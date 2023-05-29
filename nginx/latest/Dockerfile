FROM --platform=$TARGETOS/$TARGETARCH nginx:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt update
RUN apt install -y iproute2 

# Setup user
RUN useradd -m -d /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

# Copy required nginx config
COPY ./nginx.conf /etc/nginx/nginx.conf

# Setup entrypoint
COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]