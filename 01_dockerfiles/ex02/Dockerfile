# 1. Create a new rails app in this folder called "app" by running: 'rails new app'
# 2. Test that it is working locally, run: 'app/bin/rails server'
# 3. Navigate to localhost:3000 on a browser. It works!

# 4. Build the base image:
# docker build -t ft-rails:on-build .

# 5. Build the production image that includes our app.
# docker build -t railsapp:production -f Dockerfile_app .

# 6. Run our app inside a docker container
# docker run -p 3000:3000 --rm railsapp:production
FROM ruby:3.1.2

RUN apt-get update && apt-get install -y nodejs sqlite3 npm build-essential libpq-dev yarn
RUN gem install rails
ONBUILD WORKDIR /opt/app/
ONBUILD COPY ./app /opt/app
ONBUILD RUN bundle install
ONBUILD RUN bundle update --bundler
ONBUILD RUN rake db:create
ONBUILD RUN rake db:migrate

# rake is ruby's task runner.