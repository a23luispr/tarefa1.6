FROM debian:12

RUN apt update && apt install -y net-tools procps most iproute2  iputils-ping dnsutils

RUN apt install -y bind9 dnsutils rsyslog nano

RUN apt clean && rm -rf /var/lib/apt/lists/*

RUN sed 's/^OPTIONS=.*/OPTIONS="-u bind -4"/' /etc/default/named

COPY entrypoint.sh /entrypoint.sh

RUN chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]

RUN mkdir -p /var/log/bind 
RUN touch /var/log/bind/query.log 
RUN touch /var/log/bind/update.log 
RUN chown bind /var/log/bind -R


