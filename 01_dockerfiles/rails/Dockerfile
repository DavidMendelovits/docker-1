FROM ruby:2.5.1

RUN apt-get -y update && apt-get -y upgrade && \
    apt-get install -y nodejs && \
    apt-get install sqlite3 -y && \
    gem install rails && \
    gem install bundler

ONBUILD WORKDIR   /opt/app
ONBUILD ADD       . /opt/app

ONBUILD EXPOSE 3000

ONBUILD RUN bundle install 

ONBUILD RUN rake db:migrate && \
            rake db:seed
