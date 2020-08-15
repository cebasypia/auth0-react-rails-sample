FROM ruby:2.7

RUN curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add - \
  && echo "deb https://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list \
  && apt-get update -qq \
  && apt-get install -y nodejs yarn \
  && mkdir /auth0-sample

WORKDIR /auth0-sample
COPY /Gemfile /auth0-sample/Gemfile
COPY /Gemfile.lock /auth0-sample/Gemfile.lock
RUN bundle install
COPY . /auth0-sample

EXPOSE 3000

# puma.sockを配置するディレクトリを作成
RUN mkdir -p tmp/sockets