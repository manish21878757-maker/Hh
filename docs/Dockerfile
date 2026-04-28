FROM ruby:3.2-slim
WORKDIR /site
RUN apt-get update && apt-get install -y build-essential git && rm -rf /var/lib/apt/lists/*
COPY Gemfile ./
RUN bundle install
COPY . .
RUN bundle exec jekyll build
FROM nginx:alpine
COPY --from=0 /site/_site /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
