# Matee Wiki - Tooling - Ruby

## Intro
- Various development tools (such as CocoaPods, fastlane, twine, etc) are written in [Ruby](https://www.ruby-lang.org/en/)
- Since Ruby is an interpreter we can't just make a binary of needed tools, you have to install it locally

## Ruby on macOS
- There is a default system Ruby in macOS which is limited for security reasons
- Therefore it is highly recommended to install a separate virtual environment for Ruby via environment manager
- Most popular managers are [rbenv](https://github.com/rbenv/rbenv), [rvm](https://github.com/rvm/rvm) and [chruby](https://github.com/postmodern/chruby)
- We have a good experience with rbenv

## Setup rbenv on macOS
- Make sure you don't have any other manager/Ruby installed (`which ruby` should outputs `/usr/bin/ruby` - system Ruby)
- If you have other manager/Ruby installed, look into the documentation of your manager and uninstall it completely 🙃
- Install rbenv via Homebrew: `brew install rbenv ruby-build` (if you don't have Homebrew go to https://brew.sh/)
- Now we have to make sure that both Homebrew and rbenv are loaded into your non-interactive shells
- This can be done by modifying your `~/.zshenv` file and restarting Terminal (more about zsh configuration [here](/tooling/zsh.md))
- For Homebrew: `echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshenv`
- For rbenv: `echo 'eval "$(rbenv init -)"' >> ~/.zshenv`
- Install and set a required Ruby version, for example: `rbenv install 3.2.2 && rbenv global 3.2.2`
- Now you can install and use required gems, for example: `gem install twine` 🤗

## Resources
- https://github.com/rbenv/rbenv
- https://snyk.io/blog/how-to-install-ruby-in-mac-os/
