# Install Ruby and Rails on Windows 10, Ubuntu, and OS X
This is a guide to install Ruby and the web development framework Rails on Windows 10, OS X 10.11 "El Capitan", and Ubuntu 16.04 "Xenial Xerus".

## Install Ruby and Rails on Windows 10
1. Join the [Windows Insider](https://insider.windows.com/) program by Microsoft.
2. Update your Windows via the [Windows 10 Upgrader](https://support.microsoft.com/help/12387/windows-10-update-history) and **Settings > Update & Security > Windows Update**.
2. Enable the *Developer Mode* in **Settings > Update & Security > For Developers**.
3. Install the *Windows Subsystem for Linux* in **Control Panel > Programs and Features > Turn Windows Features On or Off**.
4. Run *bash* form your **Start Menu** and follow the installation process. The password you set for your user account will be your sudo password. Do not lose it!
5. Run *Bash on Ubuntu for Windows* from your *Start Menu*. It got an Ubuntu logo now.
6. You are now in a basic Ubuntu 14.04 environment in Windows 10 and are able to run Linux applications!
7. From this point on you can follow the instructions for Ubuntu.
8. There might be some premission error with bundler which you can fix with `chmod +t -R ~/.bundle` inside the folder of the Rails project.
9. The local development server will also be reachable in your Windows environment on *localhost:3000*.

## Install Ruby and Rails on Ubuntu 16.04
1. Update your system with `sudo apt-get update` and `sudo apt-get dist-upgrade` and clean up with `sudo apt-get autoclean`.
2. Install a bunch of dependencies with `sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev python-software-properties libffi-dev`.
3. Go to your home directory with `cd` and get rbenv and its ruby-build plugin via `git clone https://github.com/rbenv/rbenv.git ~/.rbenv` and `git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build`. Import them to your shell with `echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.bashrc`, `echo 'eval "$(rbenv init -)"' >> ~/.bashrc`, and `echo 'export PATH="$HOME/.rbenv/plugins/ruby-build/bin:$PATH"' >> ~/.bashrc`. Then reload your shell with `exec $SHELL`.
4. Now it is time to get Ruby with `rbenv install 2.3.1` and point your shell to it with `rbenv global 2.3.1`. Check if it worked with `ruby -v` and `gem -v`.
5. Update your gems with `gem update --system` and `gem update`. Also get bundler with `gem install bundler`. Do `rbenv rehash` afterwards.
6. Modern Rails has a lot of depencencies to JavaScript so we need to get Node.js (including npm) via `curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -` and `sudo apt-get install nodejs`. Check if it works with `node -v` and `npm -v`
7. Now finally we get Rails with `gem install rails -v 4.2.7` and `rbenv rehash`. Check if it works with `rails -v`.
8. The final check will be done with `rails new anapp`, followed by `cd anapp`, and `rails s`. The local development server will be reachable on *localhost:3000*.

## Install Ruby and Rails on OS X 10.11
1. Update your system via **App Store** > **Updates**.
2. Install Homebrew with `ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`. You enter all this commands into Terminal or iTerm.
3. Install rbenv and its ruby-build plugin via Homebrew with `brew install rbenv ruby-build`. Import them to your shell with `echo 'if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi' >> ~/.bash_profile` and `source ~/.bash_profile`.
4. Now it is time to get Ruby with `rbenv install 2.3.1` and point your shell to it with `rbenv global 2.3.1`. Check if it worked with `ruby -v` and `gem -v`. If something does not work close Terminal or iTerm completly, start it again, and try again.
5. Update your gems with `gem update --system` and `gem update`. Also get bundler with `gem install bundler`. Do `rbenv rehash` afterwards.
6. Modern Rails has a lot of depencencies to JavaScript so we need to get Node.js (including npm) via Homebrew with `brew install node`. Check if it works with `node -v` and `npm -v`
7. Now finally we get Rails with `gem install rails -v 4.2.7` and `rbenv rehash`. Check if it works with `rails -v`.
8. The final check will be done with `rails new anapp`, followed by `cd anapp`, and `rails s`. The local development server will be reachable on *localhost:3000*.


## Other Versions
If you want to install other versions than given above you can do that. If you know the version you need, then just replace that version number with those I gave. If you are not sure which versions are avaivable then do:
* `rbenv install --list` for Ruby
* `gem list rails --remote --all` for Rails

For the case that you want to use the more current but less stable Node.js 6 do this instead of the given above:
+ `curl --silent --location https://rpm.nodesource.com/setup_6.x | bash -`.

# Install and use PostgreSQL with Ruby on Rails with OS X
1. Update your system via **App Store** > **Updates**.
2. Install [Postgress.app](http://postgresapp.com/) with normal drag and drop install procedure and start it.
3. Install the pg gem manually (not with bundler) with `gem install pg -- --with-pg-config=/Applications/Postgres.app/Contents/Versions/latest/bin/pg_config`.
4. Your PostgreSQL database is now running at *localhost:5432*.
