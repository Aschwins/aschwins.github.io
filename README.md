# aschwins.github.io

## Development

How to set up development for this site. Make sure you have rbenv installed and have a Ruby version installed. In this example we'll use version 2.7.2.

```sh
export RBENV_VERSION=2.7.2

# install bundler if you havent already for the current ruby version
gem install bundler

# install all the dependencies in the Gemfile (creates Gemfile.lock)
bundle install
```