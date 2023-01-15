FROM ruby:2.7.0

# throw errors if Gemfile has been modified since Gemfile.lock
RUN apt-get update -qq && apt-get install -y nodejs postgresql-client npm \
&& rm -rf /var/lib/apt/lists/* \
&& npm install --global yarn

RUN mkdir /api
WORKDIR /api

# コンテナー起動時に毎回実行されるスクリプトを追加
COPY ../../api/entrypoint.sh /usr/bin/
RUN chmod +x /usr/bin/entrypoint.sh
ENTRYPOINT ["entrypoint.sh"]

COPY ../../api/Gemfile /api/
COPY ../../api/Gemfile.lock /api/
RUN bundle install

# イメージ実行時に起動させる主プロセスを設定
CMD ["rails", "server", "-p", "8000", "-b", "0.0.0.0"]
