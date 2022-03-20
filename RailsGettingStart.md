# Rails Getting Start

## Tutorials

[Learn Ruby on Rails for Beginners](https://www.ruby-lang.org/en/documentation/)

## Editor Setup

- VSCode
  - [Ruby](https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby)
  - [VSCode Ruby](https://marketplace.visualstudio.com/items?itemName=wingrunr21.vscode-ruby)
  - [Rails](https://marketplace.visualstudio.com/items?itemName=bung87.rails)
  - [vscode-gemfile](https://marketplace.visualstudio.com/items?itemName=bung87.vscode-gemfile)
  - [Slim](https://marketplace.visualstudio.com/items?itemName=sianglim.slim)

## Install Ruby

Follow steps from https://gorails.com/setup.

## Installing Ruby in WSL (Ubuntu20.04 on Windows 10)

Ref: https://gorails.com/setup/windows/10

The first step is to install some dependencies for Ruby.

```bash
sudo apt-get update
sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev
```

Next we're going to be installing Ruby with a version manager called Rbenv.

Installing with rbenv is a simple two step process. First you install rbenv, and then ruby-build:

```bash
cd ~
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
exec $SHELL

git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc
exec $SHELL
```

To install Ruby and set the default version:

```bash
# list latest stable versions:
rbenv install -l

# list all local versions:
rbenv install -L

# install a Ruby version:
rbenv install 3.0.3

# set Ruby version:
rbenv global 3.0.3
```

Confirm the default Ruby version matches the version you just installed.

```bash
ruby -v
```

The last step is to install Bundler

```bash
gem install bundler
```

rbenv users need to run `rbenv rehash` after installing bundler.

## Install NodeJS(v16) and Yarn

Since Rails ships with so many dependencies these days, we're going to need to install a Javascript runtime like NodeJS and a package manager called Yarn.

To install NodeJS and Yarn, we're going to add it using the official repository:

```bash
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -
echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list

sudo apt update
sudo apt install -y nodejs yarn
```

## Installing Rails

To install Rails v6, run the following command:

`gem install rails -v 6.1.4.4`

If you're using rbenv, you'll need to run the following command to make the rails executable available:

`rbenv rehash`

## Creating New Rails App

To create new rails app, run the following command:

`rails new <app-name>`

## Starting Rails Server

To start rails server, run the following command:

```bash
rails server
# or
rails s
```

## Creating the User Model

```bash
$ rails generate model User email:string password_digest:string
Running via Spring preloader in process 1780
      invoke  active_record
      create    db/migrate/20220213093037_create_users.rb
      create    app/models/user.rb
      invoke    test_unit
      create      test/models/user_test.rb
      create      test/fixtures/users.yml
$ rails db:migrate
Running via Spring preloader in process 1818
== 20220213093037 CreateUsers: migrating ======================================
-- create_table(:users)
   -> 0.0028s
== 20220213093037 CreateUsers: migrated (0.0034s) =============================
```

## Misc

Remove all installed gems:

```bash
for x in `gem list --no-versions`; do gem uninstall $x -a -x -I; done
```

Entering rails console mode:

`$ rails console`

Reloading rails app in console mode:

`irb(main):001:0> reload!`

## Websites

[Rubular](https://rubular.com) - a Ruby regular expression editor
