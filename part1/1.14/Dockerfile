# Build from node image
FROM debian:buster

# Set working direcotry
WORKDIR /app

# Install git and other 'needed' packages
RUN apt-get update && apt-get install -y git
RUN apt-get install -y build-essential openssl \
curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 \
libxml2-dev libxslt-dev autoconf libc6-dev ncurses-dev automake libtool bison  \
subversion nodejs npm gpg procps

# Install ruby with rvm
RUN gpg --keyserver hkp://keys.gnupg.net --recv-keys D39DC0E3
RUN curl -sSL https://get.rvm.io | bash -s
SHELL [ "/bin/bash", "-l", "-c" ]
RUN rvm install 2.6.0

# Clone exercise project
RUN git clone https://github.com/docker-hy/rails-example-project.git .

# Ruby gems
RUN gem install bundler
RUN gem install rails
RUN bundle install

# Build
RUN rails db:migrate
RUN rake assets:precompile

# Expose port
EXPOSE 3000

# And finaly run
CMD rails s
