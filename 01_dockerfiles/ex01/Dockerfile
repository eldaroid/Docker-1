# FROM debian

# ENV TS3SERVER_LICENSE=accept
# ENV VERSION=TSV=3.0.13.8

# WORKDIR /home/teamspeak

# RUN apt-get update -y && \
#     apt-get upgrade -y

# RUN apt-get install -y wget bzip2 && \
#     wget http://dl.4players.de/ts/releases/3.6.1/teamspeak3-server_linux_amd64-3.6.1.tar.bz2 && \
#     tar -xvf teamspeak3-server_linux_amd64-3.6.1.tar.bz2 && \
#     mv teamspeak3-server_linux_amd64 /opt/teamspeak && \
#     rm teamspeak3-server_linux_amd64-$VERSION.tar.bz2

# RUN chmod +x /entrypoint.sh

# #  9987 default voice
# # 10011 server query
# # 30033 file transport

# # Load in all of our config files.
# ADD entrypoint.sh /entrypoint.sh

# EXPOSE 9987/udp 10011 30033

# ENTRYPOINT [ "/entrypoint.sh" ]

FROM debian

ENV TS3SERVER_LICENSE=accept
ENV VERSION=3.9.1

WORKDIR /home/ts

EXPOSE 9987/udp 10011 30033

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y bzip2 wget && \
    wget https://files.teamspeak-services.com/releases/server/3.9.1/teamspeak3-server_linux_amd64-3.9.1.tar.bz2 && \
    tar -xvf teamspeak3-server_linux_amd64-3.9.1.tar.bz2

WORKDIR /home/ts/teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh

#Starting with TeamSpeak 3.1.0, the license agreement must be accepted before you can run TeamSpeak. 
#To accept the agreement, you need to do one of the following:
#Add the following to your run command: -e TS3SERVER_LICENSE=accept to pass an environment variable

#download server https://www.teamspeak.com/en/downloads/#server

#docker build -t ts3-image . - Чтоб простроить
#docker run -it --rm -p=9987:9987/udp  -p=10011:10011 -p=30033:30033 ts3-image - Чтоб запустить
