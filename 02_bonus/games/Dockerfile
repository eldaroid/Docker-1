FROM debian

# ПЕРЕМЕЩАТЬСЯ ПО ЦИФРАМ
# RUN apt-get update -y && apt-get install greed -y

# 2048
# RUN apt-get update -y && apt-get upgrade -y && apt install build-essential -y && apt-get install wget -y && wget https://raw.githubusercontent.com/mevdschee/2048.c/master/2048.c

# МАШИНКИ
# RUN apt-get update -y && apt-get install moon-buggy -y

# ЗМЕЙКА
# RUN apt-get update -y && apt-get install nsnake -y  

#ПАКМАН
# RUN apt-get update -y && apt-get install pacman4console -y

#ТЕТРИС
RUN apt-get update -y && apt-get install bastet -y

ENTRYPOINT /bin/bash 

# How to build it?
# docker build -t a00 .

# How to run it?
# docker run --rm -ti a00

# ПЕРЕМЕЩАТЬСЯ ПО ЦИФРАМ
# in folder /usr/games run  command ./greed

# 2048
# in folder /usr/games run gcc -o 2048 2048.c , then ./2048

# МАШИНКИ
# in folder /usr/games run ./moon-buggy and U can use SPACE for jumping and K for killind, to exit touch Control + C

# ЗМЕЙКА
# in folder /usr/games run  command ./nsnake, to exit touch Control + C

#ПАКМАН
# in folder /usr/games run  command ./pacman4console, to exit touch Control + C

#ТЕТРИС
# in folder /usr/games run  command ./bastet, to exit touch Control + C

