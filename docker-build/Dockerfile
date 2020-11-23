FROM scratch
ADD alpine-minirootfs-3.12.1-x86_64.tar.gz /
COPY localtime /etc/localtime

# Add a new non-root user
ARG USERNAME=mydocker
ARG USER_UID=1000
ARG USER_GID=$USER_UID

RUN apk --no-cache add sudo && \
	addgroup -g $USER_GID $USERNAME && \
	adduser -u $USER_UID -G $USERNAME -h /home/$USERNAME -D $USERNAME && \
	echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME && \
	chmod 0440 /etc/sudoers.d/$USERNAME && \
	mkdir /home/$USERNAME/project/

USER $USERNAME
ENV HOME /home/$USERNAME
WORKDIR /home/$USERNAME

CMD ["/bin/sh"]
