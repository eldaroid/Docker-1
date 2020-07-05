  
# FROM ubuntu:16.04

# SHELL ["/bin/sh", "-c"],

# # Default to supporting utf-8
# ENV LANG=C.UTF-8

# # Install required packages
# RUN apt-get update -q \
#     && DEBIAN_FRONTEND=noninteractive apt-get install -yq --no-install-recommends \
#       ca-certificates \
#       openssh-server \
#       wget \
#       apt-transport-https \
#       vim \
#       tzdata \
#       nano \
#       less \
#     && rm -rf /var/lib/apt/lists/* \
#     && sed 's/session\s*required\s*pam_loginuid.so/session optional pam_loginuid.so/g' -i /etc/pam.d/sshd

# # Remove MOTD
# RUN rm -rf /etc/update-motd.d /etc/motd /etc/motd.dynamic
# RUN ln -fs /dev/null /run/motd.dynamic

# # Copy assets
# COPY RELEASE /
# RUN /assets/setup

# # Allow to access embedded tools
# ENV PATH /opt/gitlab/embedded/bin:/opt/gitlab/bin:/assets:$PATH

# # Resolve error: TERM environment variable not set.
# ENV TERM xterm

# # Expose web & ssh
# EXPOSE 443 80 22

# # Define data volumes
# VOLUME ["/etc/gitlab", "/var/opt/gitlab", "/var/log/gitlab"]

# # Wrapper to handle signal, trigger runit and reconfigure GitLab
# CMD ["/assets/wrapper"]

# HEALTHCHECK --interval=60s --timeout=30s --retries=5 \
# CMD /opt/gitlab/bin/gitlab-healthcheck --fail --max-time 10




FROM ubuntu:16.04

RUN apt-get update && \
    apt-get upgrade -y && \
    # apt-get install gitlab-ee && \
    apt-get install -y ca-certificates openssh-server wget postfix

RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod 777 script.deb.sh && ./script.deb.sh && apt-get install -y gitlab-ce

RUN apt update && apt install -y tzdata && \
  apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

EXPOSE 443 80 22

ENTRYPOINT (/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null