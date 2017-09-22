# Ekumenlabs.com

## Enviroment Setup

First of all, **do not** work on the `master` branch of this repository. Make sure to checkout the `middleman` branch and use it as base for your work.

### Install **Ruby version 2.2.0**

The recommended way to do so is using [RVM](https://rvm.io/). You can follow their [install guide](https://rvm.io/rvm/install).

With RVM installed, you can now install the required Ruby version.

```
rvm install ruby-2.2.0
rvm --ruby-version use 2.2.0
```

This creates a `.ruby-version` file that sets the Ruby version to use each time you enter this folder.

To check the version used, you can use either:
```
ruby -v
```
or
```
rvm list rubies
```

As a double check, the ruby version is also declared in the `Gemfile`.

### Install nodejs

This is required by the gem Nokogiri. You can install NodeJS by doing the following:

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Install the Bundler

With Ruby installed and set in the correct version, enter the following:

```
gem install bundler
bundle install
```

## Run the Website

The following command makes the website run in the localhost. Check the `config.rb` file for the address.

```
middleman
```

## Build the Website

To build a static version of the Website, run:

```
middleman build
```

The output is inside the `build` folder.

From the [Middleman Website](https://middlemanapp.com/basics/build-and-deploy)
> This will create a static file for each file located in your source folder. Template files will be compiled, static files will be copied and any enabled build-time features (such as compression) will be executed. Middleman will automatically clean out files from the build directory for you that are left over from earlier builds but would no longer be produced.

## Deploy the Website

You can deploy the website by making a Pull Request targetting the middleman branch. The website should be deployed automatically.
