# ruby project deployment

You can clone the [docker-hy/material-applications/rails-example-project](https://github.com/docker-hy/material-applications/tree/main/rails-example-project)
to follow its README instruction. 

Then you do the following:
- write the Docker file
- build the image
- spin up a container 
- go to your fav browser to check out the localhost:3000


```Docker
FROM ruby:3.1.0

EXPOSE 3000

WORKDIR /usr/src/app

# Install the correct bundler version
RUN gem install bundler:2.3.3

# Copy the files required for dependencies to be installed
COPY Gemfile* ./

# install all dependencies
RUN bundle install

# copy the source code
COPY . .

# We pick the production mode since we have no intention of developing the software inside the container.
# Run database migrations by following instructions from README
RUN rails db:migrate RAILS_ENV=production

# Precompile assets by following instructions from README
RUN rake assets:precompile

# And finally the command to run the application
CMD ["rails", "s", "-e", "production"]
```

Now you build your images and spin up container.

```bash
# create the image
docker image build -t rails-project .

# spin up container 
docker container run -p 3000:3000 \ rails-project
```




