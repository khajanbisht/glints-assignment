FROM ubuntu:18.04

RUN DEBIAN_FRONTEND="noninteractive" apt-get update -y \
    && apt-get install wget net-tools tzdata keyboard-configuration openssh-server -y 
RUN echo "Asia/Kolkata" | tee /etc/timezone
RUN dpkg-reconfigure --frontend noninteractive tzdata
RUN apt-get install tigervnc-standalone-server tigervnc-common tigervnc-viewer xfce4 -y
RUN apt-get install novnc net-tools git -y
RUN echo 'root:q' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config
RUN echo 'PermitRootLogin yes' | cat >> /etc/ssh/sshd_config
RUN mkdir $HOME/.vnc
COPY xstartup $HOME/.vnc/xstartup
EXPOSE 5901
ENTRYPOINT service ssh restart && vncserver -SecurityTypes None,TLSNone -fg