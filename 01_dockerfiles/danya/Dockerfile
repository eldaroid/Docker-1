FROM ubuntu:18.04

RUN apt -y update && \
	apt -y upgrade && \
	apt -y install curl \
		openssh-server \
		tzdata \
		postfix \
		ca-certificates && \
	apt -y clean

ENV TERM xterm

RUN curl --fail \
		https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh | \
		bash && \
	apt -y install gitlab-ce && \
	apt -y clean

ARG EXTERNAL_URL="192.168.99.100"
ARG HTTPS_PORT="8443"
ARG GITLAB_OMNIBUS_CONFIG="external_url 'https://${EXTERNAL_URL}/'; letsencrypt['enable'] = false"

EXPOSE 22 80 ${HTTPS_PORT}

RUN mkdir -p /etc/gitlab/ssl && \
	chmod 755 /etc/gitlab/ssl && \
	openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/gitlab/ssl/${EXTERNAL_URL}.key -out /etc/gitlab/ssl/${EXTERNAL_URL}.crt -subj "/C=RU/ST=Moscow/L=Moscow/O=21-school/OU=docker-1/CN=${EXTERNAL_URL}" && \
	chmod 600 /etc/gitlab/ssl/* && \
	sed -i "s/\# letsencrypt\['enable'\] = nil/letsencrypt\['enable'\] = false/" /etc/gitlab/gitlab.rb && \
	sed -i "s/external_url 'http:\/\/gitlab.example.com'/external_url 'https:\/\/${EXTERNAL_URL}:${HTTPS_PORT}'/" /etc/gitlab/gitlab.rb && \
	sed -i "s/# nginx\['redirect_http_to_https'\] = false/nginx\['redirect_http_to_https'\] = true/" /etc/gitlab/gitlab.rb

RUN mkdir -p /run/sshd

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && \
				/usr/sbin/sshd && \
				gitlab-ctl reconfigure && \
				tail -f /dev/null

# How to build it? 
# docker build -t gitlab .

# How to run it?
# docker run -it --rm -p 8080:80 -p 8022:22 -p 8443:8443 --privileged gitlab

# flags for docker-machine create: docker-machine create --driver virtualbox --virtualbox-memory "2048" --virtualbox-cpu-count "2" Char
# eval $(docker-machine env Char)

# how to clone with ssh:   ssh -T -p 8022 git@192.168.99.100
#                          git clone ssh://git@192.168.99.100:8022/root/test_project.git

# how to clone with https: git config --global http.sslVerify false
#                          git clone https://192.168.99.100:8443/root/test_project.git

