FROM debian

RUN apt-get update && \
	apt-get upgrade -y && \
	apt-get install -y vim gcc

ENTRYPOINT /bin/bash 

# docker build -t cenv .
# docker run --rm -it cenv