FROM debian:sid

RUN apt-get update
# installing git, golang sqlite openssl
RUN apt-get install --no-install-recommends build-essential ca-certificates \
	git golang-go sqlite libsqlite3-dev openssl openssh-server -y && \
	mkdir -p /root/go/src/github.com/gogs && \
	cd /root/go/src/github.com/gogs && \
	git clone --recurse-submodules -b develop https://github.com/gogs/gogs && \
	cd gogs && \
	go build -v -tags 'sqlite'

# run gogs and login as root
ENV USER="root"
WORKDIR /root/go/src/github.com/gogs/gogs
# port 3000
EXPOSE 3000 22 
USER root
CMD ["./gogs", "web"]
