FROM alpine

RUN apk update && apk upgrade && apk add vim -y && rm -rf /var/lib/apt/lists

ENTRYPOINT ["vim"]

# docker built --tag image .
# docker run -it image
# https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management
# rm -rf /var/lib/apt/lists - поскольку когда мы прописываем apk 
# update - он получает информацию о самых новых версиях всех пакетов 
# updATE сам по себе ничего не обновляет
# apk upgrade -  обновляет все пакет, которые уже установлены
