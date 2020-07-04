FROM debian

ENV TS3SERVER_LICENSE=accept
ENV TSV=3.12.1

WORKDIR /home/ts

EXPOSE 9987/udp 10011 30033

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y bzip2 wget

ADD http://dl.4players.de/ts/releases/${TSV}/teamspeak3-server_linux_amd64-${TSV}.tar.bz2 ./

RUN    tar -xvf teamspeak3-server_linux_amd64-$TSV.tar.bz2

WORKDIR /home/ts/teamspeak3-server_linux_amd64

ENTRYPOINT sh ts3server_minimal_runscript.sh

#Starting with TeamSpeak 3.1.0, the license agreement must be accepted before you can run TeamSpeak. 
#To accept the agreement, you need to do one of the following:
#Add the following to your run command: -e TS3SERVER_LICENSE=accept to pass an environment variable

#download server https://www.teamspeak.com/en/downloads/#server

#docker build -t ts3-image . - Чтоб простроить
#docker run -it --rm -p 9987:9987/udp -p 10011:10011 -p 30033:30033 ts3-image - Чтоб запустить
#log on with (docker-machine ip Char):9987