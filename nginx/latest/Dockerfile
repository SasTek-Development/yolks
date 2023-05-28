FROM --platform=$TARGETOS/$TARGETARCH nginx:latest

ENV DEBIAN_FRONTEND noninteractive

RUN apt update
RUN apt install -y software-properties-common iproute2 
RUN add-apt-repository ppa:ondrej/php 

# RUN apt update && apt -y install php8.1 php8.1-{common,cli,gd,mysql,mbstring,bcmath,xml,fpm,curl,zip,fpm}
RUN useradd -m -d /home/container container

USER container
ENV USER=container HOME=/home/container
WORKDIR /home/container

COPY ./../nginx.conf /etc/nginx/nginx.conf

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]