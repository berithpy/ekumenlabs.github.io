# Ekumenlabs.com

## Environment Setup

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

> The Ekumen Website is an [Organization GitHub Page](https://help.github.com/articles/user-organization-and-project-pages/), therefore, its static source files can be found in the `master` branch. Any push made into `master` will reflect into the website, so be careful!

Make sure you are in the `middleman` branch. This needs to be the starting point of your work branches.

```
git checkout middleman
```

Run the website locally by doing:

```
middleman
```

Check the terminal or the `config.rb` file for the address.

When you make a Pull Request with your changes, make sure to change its base to the `middleman` branch. After this has been properly reviewed and merged, the website needs to be manually built and deployed.

To build the website, do:

```
middleman build
```

The output is inside the `build` folder. This folder is ignored in the `middleman` branch.

**Be careful:** Keep in mind that any changes you made will be built, even uncommited ones. Make sure you have the updated `middleman` branch with the latest changes that you want to deploy and nothing else.

From the [Middleman Website](https://middlemanapp.com/basics/build-and-deploy)
> This will create a static file for each file located in your source folder. Template files will be compiled, static files will be copied and any enabled build-time features (such as compression) will be executed. Middleman will automatically clean out files from the build directory for you that are left over from earlier builds but would no longer be produced.

After building, deploy the website doing:

```
middleman deploy
```

This command will automatically push the `build` folder into the `master` branch, which will update the website. Note that the website won't load until the deploy is finished.

The commit history you will see in the `master` branch depends on the `build` folder of your local installation, so don't worry about it. The important history lies in the `middleman` branch.

## Rollback

Something went wrong? Don't worry. You can always [revert](https://github.com/blog/2019-how-to-undo-almost-anything-with-git) the `middleman` branch into a previous and stable state, and then build and deploy the website again.

```
git checkout middleman
git revert <stable-commit-SHA>
middleman build
middleman deploy
```

If you need to fix something directly on the `master` branch, you can do it. The website shows what's in the `master` branch after all.

```
git checkout master
git commit -m "My changes"
git push -f origin master
```

Keep in mind that working directly on the `master` is discouraged and should be avoided. All the work done should have the `middleman` branch as a starting point.
