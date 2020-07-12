FROM ubuntu:18.04

# openssh-server - openssh-server
# tzdata - https://habr.com/ru/post/130401/
# postfix - https://ru.wikipedia.org/wiki/Postfix#:~:text=Postfix%20%E2%80%94%20%D0%B0%D0%B3%D0%B5%D0%BD%D1%82%20%D0%BF%D0%B5%D1%80%D0%B5%D0%B4%D0%B0%D1%87%D0%B8%20%D0%BF%D0%BE%D1%87%D1%82%D1%8B%20(MTA,%D0%BE%D0%B1%D0%B5%D1%81%D0%BF%D0%B5%D1%87%D0%B5%D0%BD%D0%B8%D0%B5%D0%BC%2C%20%D1%81%D0%BE%D0%B7%D0%B4%D0%B0%D0%B2%D0%B0%D0%BB%D1%81%D1%8F%20%D0%BA%D0%B0%D0%BA%20%D0%B0%D0%BB%D1%8C%D1%82%D0%B5%D1%80%D0%BD%D0%B0%D1%82%D0%B8%D0%B2%D0%B0%20Sendmail.
# ca-certificates - https://en.wikipedia.org/wiki/Certificate_authority
# apt -y clean - https://ru.stackoverflow.com/questions/638/%D0%9E%D1%87%D0%B8%D1%81%D1%82%D0%BA%D0%B0-%D0%BA%D1%8D%D1%88%D0%B0-apt-get

RUN apt -y update && \
	apt -y upgrade && \
	apt -y install curl \
		openssh-server \
		tzdata \
		postfix \
		ca-certificates && \
	apt -y clean

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

# https://docs.gitlab.com/omnibus/maintenance/

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