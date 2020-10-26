# no frills repository minecraft server #
FROM ubuntu:latest
LABEL maintainer="Tadaen Sylvermane <jmgibson81@gmail.com>"

# add init service #

ADD minecraft /etc/init.d/

# install & cleanup #

RUN apt update && \
		apt full-upgrade -y && \
		apt install -y \
		--no-install-recommends \
		openjdk-14-jre-headless \
		screen \
		wget \
		cron && \
		apt clean && \
		rm -r /var/lib/apt/lists/* && \
		chmod 755 /etc/init.d/minecraft
		
# get current minecraft server jar file & configure #

RUN wget -O - https://www.minecraft.net/en-us/download/server \
		> /tmp/mcserver && \
		grep minecraft_server.[1-9] /tmp/mcserver > /tmp/mcservertype && \
		while IFS='"' read -r trash1 info trash2 ; do \
		wget -O /root/server.jar "$info" && break ; done < /tmp/mcservertype && \
		rm /tmp/mcserver /tmp/mcservertype

ADD rootcrontab /var/spool/cron/crontabs/root
RUN chmod 600 /var/spool/cron/crontabs/root && \
		chown root:crontab /var/spool/cron/crontabs/root
