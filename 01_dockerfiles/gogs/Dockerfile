FROM debian

RUN ["apt-get", "update"]

RUN ["apt-get", "install", "-y", "golang", "sqlite3", "git"]

ENV USER root

ENV GOPATH /

WORKDIR src/github.com/gogits

RUN ["git", "clone", "--depth=1", "-b", "develop", "https://github.com/gogits/gogs"]

RUN ["go", "get", "-u", "-tags", "sqlite", "github.com/gogits/gogs"]

WORKDIR gogs

RUN ["go", "build", "-tags", "sqlite"]

EXPOSE 3000

ENTRYPOINT ["./gogs", "web"]
