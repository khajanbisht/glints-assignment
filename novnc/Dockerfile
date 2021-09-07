FROM ubuntu:18.04

RUN DEBIAN_FRONTEND="noninteractive" apt-get update -y && apt-get -y install tzdata openssh-server -y
RUN echo "Asia/Kolkata" | tee /etc/timezone
RUN dpkg-reconfigure --frontend noninteractive tzdata
RUN apt-get install novnc net-tools git sshpass -y
WORKDIR /usr/share/novnc
RUN cd utils && git clone https://github.com/novnc/websockify websockify
EXPOSE 6080 
ENTRYPOINT ./utils/launch.sh --vnc localhost:5901
 