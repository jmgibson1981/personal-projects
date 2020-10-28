# no frills repository installation of mariadb-server #
FROM ubuntu:latest
LABEL maintainer="Tadaen Sylvermane <jmgibson81@gmail.com>"

# install & cleanup #

RUN apt update && \
		apt full-upgrade -y && \
		apt install -y \
		--no-install-recommends \
		rsyslog \
		nano \
		mariadb-server && \
		apt clean && \
		rm -r /var/lib/apt/lists/*

# create configuration files #

ADD 99-kodi-optimize.cnf /etc/mysql/mariadb.conf.d/


