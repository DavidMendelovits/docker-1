# docker build -t ft-rails:5.0.2-on-build .
FROM              ruby:2.5.1

# Install rails, sqlite3, and node

RUN               apt-get update && gem install rails && gem install bundler
RUN				  apt-get install nodejs -y && apt-get install sqlite3 -y
RUN               mkdir /opt/app

# add application to correct folder

ONBUILD WORKDIR   /opt/app
ONBUILD ADD       . /opt/app

# Default portnumber

ONBUILD EXPOSE    3000

# Run bundle install to install all necessary gems

ONBUILD RUN       bundle install

# seeds the database.

ONBUILD RUN       rake db:migrate && rake db:seed
