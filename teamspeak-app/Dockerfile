FROM ubuntu:20.04

RUN apt-get update && apt-get install -y \
    wget \
    bzip2 \
    && rm -rf /var/lib/apt/lists/*

# Download the latest TeamSpeak server (update version as needed)
RUN wget -O teamspeak.tar.bz2 "https://files.teamspeak-services.com/releases/server/3.13.7/teamspeak3-server_linux_amd64-3.13.7.tar.bz2" \
    && tar -xjf teamspeak.tar.bz2 -C /opt/ \
    && rm teamspeak.tar.bz2
WORKDIR /opt/teamspeak3-server_linux_amd64

COPY src/entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011

ENTRYPOINT ["/entrypoint.sh"]