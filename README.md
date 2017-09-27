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

## Workflow

Make sure you checkout the `middleman` branch. This needs to be the starting point of your work branches.

> The Ekumen Website is an [Organization GitHub Page](https://help.github.com/articles/user-organization-and-project-pages/), therefore, its static source files can be found in the `master` branch. Any push made into `master` will reflect into the Website, so be careful!

Once in your working branch, you can make changes to the website. Run the website locally to check that everything is working as expected.

Make a Pull Request and point it to the `middleman` branch. After this has been properly reviewed and merged, the Website needs to be manually built and deployed.

## Run the Website

The following command makes the website run in the localhost. Check the terminal or the `config.rb` file for the address.

```
middleman
```

## Build the Website

To build a static version of the Website, run:

```
middleman build
```

The output is inside the `build` folder. This folder is ignored in the `middleman` branch.

Keep in mind that any changes you made will be built, even uncommited ones.

From the [Middleman Website](https://middlemanapp.com/basics/build-and-deploy)
> This will create a static file for each file located in your source folder. Template files will be compiled, static files will be copied and any enabled build-time features (such as compression) will be executed. Middleman will automatically clean out files from the build directory for you that are left over from earlier builds but would no longer be produced.

## Deploy the Website

**Be careful:** Before deploying, you need to manually build the static files of the website, using the previously mentioned command. Make sure you have the updated `middleman` branch with the lastest changes that you want to deploy and nothing else.

You can deploy the website by doing:

```
middleman deploy
```

This command will automatically push the `build` folder into the `master` branch, which will update the website. Note that the website won't load until the deploy is finished.

The commit history you will see in the `master` branch depends on the `build` folder of each user, so don't worry about it. The important history lies in the `middleman` branch.

## Rollback

Something went wrong? Don't worry. You can always revert the `middleman` branch into a previous and stable state. Once this is done, you can build the website and deploy it again following the previously mentioned steps. This should be the correct workflow when it comes fixing problems.

In dire situations, you can commit and push directly into `master` and the website will reflect this change. Still, this is strongly discouraged and should be avoided at all cost.
