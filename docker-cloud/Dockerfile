FROM ruby:alpine

EXPOSE 8080
CMD ["bundle", "exec", "ruby", "myapp.rb", "-o", "0.0.0.0", "-p", "8080"]
WORKDIR /app
ADD / /app/
RUN ["bundle", "install", "--deployment", "--without", "development", "test"]
