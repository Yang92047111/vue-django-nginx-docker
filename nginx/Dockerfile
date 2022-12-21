# Image
FROM nginx:stable

# Add config
COPY default.conf /etc/nginx/conf.d/default.conf

ARG TZ=Etc/UTC

RUN apt-get update

# setting ssh
RUN apt-get install -y openssh-server

RUN echo "Port 22" >> /etc/ssh/sshd_config
RUN echo "PasswordAuthentication yes" >> /etc/ssh/sshd_config
RUN echo "PermitRootLogin yes" >> /etc/ssh/sshd_config

RUN service ssh start

EXPOSE 22

# set password, {username}:{password}
RUN echo 'root:spielab107' | chpasswd

# install apt-get
RUN apt-get install -y vim
RUN apt-get install -y tree

CMD ["nginx", "-g", "daemon off;"]

