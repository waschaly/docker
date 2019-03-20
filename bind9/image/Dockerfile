FROM debian:latest

MAINTAINER "Wolf-Agathon Schaly" 

# COPY --from=add-apt-repositories /etc/apt/trusted.gpg /etc/apt/trusted.gpg

# COPY --from=add-apt-repositories /etc/apt/sources.list /etc/apt/sources.list

RUN groupadd -g 501 bind 
RUN useradd -c "docker microservice BIND9" -d /var/bind -g 501 -s /bin/false -u 501 bind

RUN rm -rf /etc/apt/apt.conf.d/docker-gzip-indexes \
 && apt-get update \
 && DEBIAN_FRONTEND=noninteractive apt-get install -y \
    bind9 bind9-host dnsutils apt-utils \
	less vim

# RUN mkdir -p /etc/bind/zone
RUN mkdir -p /run/bind && chown bind:bind /run/bind
RUN mkdir -p /var/bind && chown bind:bind /var/bind && chmod 0750 /var/bind

ADD entrypoint.sh /entrypoint.sh
ADD named.conf.tar /etc/bind

EXPOSE 53/udp 53/tcp

ENTRYPOINT /entrypoint.sh 
