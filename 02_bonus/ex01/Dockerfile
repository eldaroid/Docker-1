# FROM debian

# LABEL maintainer="gmolin@student.hive.fi"

# RUN apt-get update 
# RUN apt-get install default-jdk -y
# RUN apt-get install screen -y
# RUN apt-get install wget -y

# RUN mkdir minecraft && cd minecraft

# RUN wget -O minecraft_server.jar https://s3.amazonaws.com/Minecraft.Download/versions/1.7.4/minecraft_server.1.7.4.jar

# EXPOSE 25565

# RUN network="bridge"

# RUN java -Xmx1024M -Xms1024M -jar minecraft_server.jar

# CMD bash
# # How to build / run it?
# # docker build -t b02 .
# # docker run -it --rm -p 8080:80 b02

FROM debian

RUN apt-get update && apt-get upgrade -y && apt-get install -y wget default-jre

WORKDIR minecraft

RUN wget https://launcher.mojang.com/mc/game/1.13/server/d0caafb8438ebd206f99930cfaecfa6c9a13dca0/server.jar

RUN echo 'eula=true' > eula.txt

EXPOSE 25565

ENTRYPOINT java -Xmx1024M -Xms1024M -jar server.jar