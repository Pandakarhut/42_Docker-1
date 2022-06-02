# How to install: https://www.howtoforge.com/how-to-install-teamspeak-server-on-debian-11/

# Building the image:
# docker build -t teamspeakserver .

# Run:
# docker run --rm -p 9987:9987/udp -p 10011:10011 -p 30033:30033 teamspeakserver

# FROM [image]:default install the latest tag
FROM debian:11.3
EXPOSE 9987/udp 10011 30033
ENV TVERSION=3.13.6
RUN apt update -y && apt upgrade -y && apt install -y nano software-properties-common dirmngr apt-transport-https gnupg2 ca-certificates lsb-release debian-archive-keyring wget bzip2
RUN wget https://files.teamspeak-services.com/releases/server/${TVERSION}/teamspeak3-server_linux_amd64-${TVERSION}.tar.bz2
RUN tar -xf ./teamspeak3-server_linux_amd64-${TVERSION}.tar.bz2
RUN adduser ts3 --home /opt/teamspeak --shell /bin/bash --disabled-password
RUN mv teamspeak3-server_linux_amd64/* /opt/teamspeak/
RUN chown -R ts3:ts3 /opt/teamspeak
USER ts3
WORKDIR /opt/teamspeak
RUN touch .ts3server_license_accepted
CMD ["./ts3server_minimal_runscript.sh", "start"]
