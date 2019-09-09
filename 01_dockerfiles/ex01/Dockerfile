FROM debian

RUN apt-get update -y && apt-get upgrade -y
RUN apt-get install curl -y
RUN apt-get install bzip2 -y

# CONFIG TEAMSPEAK

#PORT 
EXPOSE 9987/udp
EXPOSE 30033
EXPOSE 10011
EXPOSE 41144

RUN useradd ts3
WORKDIR /home/t3

#ENV
ENV TS3SERVER_LICENSE="accept"

RUN curl http://dl.4players.de/ts/releases/3.3.1/teamspeak3-server_linux_amd64-3.3.1.tar.bz2 > teamspeak-server.tar.bz2 
RUN tar -xjvf teamspeak-server.tar.bz2
#RUN echo "license_accepted=1" > /home/t3/teamspeak3-server_linux_amd64/.ts3server_license_accepted
WORKDIR teamspeak3-server_linux_amd64
COPY ts3server.ini /home/t3/teamspeak3-server_linux_amd64/ts3server.ini
USER ts3
ENTRYPOINT ["sh","ts3server_minimal_runscript.sh", "inifile=ts3server.ini"]
