## Steps for setting up a ROR Project

Download and install a Ubuntu 16.04 LTS VM.
http://releases.ubuntu.com/16.04/ubuntu-16.04-desktop-amd64.iso

Make sure you have the most recent software packages with

```
sudo apt update
sudo apt upgrade
```

Clone portal repo.

```
git clone git@github.com:sithara/portal.git
```

Install development packages with `sudo apt install -y autoconf bison build-essential freetds-dev git libcurl4-openssl-dev libffi-dev libgdbm-dev libgdbm3 libncurses5-dev libpq-dev libreadline6-dev libsqlite3-dev libssl-dev libxml2-dev libxslt-dev libyaml-dev monit postfix redis-server zlib1g-dev`.

Install [rbenv](https://github.com/rbenv/rbenv), [ruby-build](https://github.com/rbenv/ruby-build) and [rbenv-aliases](https://github.com/tpope/rbenv-aliases).

```
git clone https://github.com/rbenv/rbenv.git ~/.rbenv
cd ~/.rbenv && src/configure && make -C src && cd
echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(rbenv init -)"' >> ~/.bashrc
source .bashrc
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
git clone https://github.com/tpope/rbenv-aliases.git ~/.rbenv/plugins/rbenv-aliases
```

```
rbenv install 2.3.5
rbenv alias --auto
rbenv global 2.3.5
```

Check you're now running the right version with `ruby -v`, it should show something like `ruby 2.3.5p376 (2017-09-14 revision 59905) [x86_64-linux]`.

Install necessary Ruby packages:

```
gem install bundler
rbenv rehash
bundle install --without metrics
```

## Running app locally

Run the server with `bundle exec rails server`, then navigate to http://localhost:3000/.
