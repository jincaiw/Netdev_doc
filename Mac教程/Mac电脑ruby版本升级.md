Mac自身的ruby 版本 2.x，

ruby -v可以查看版本号。

为更新到ruby的最新版本，可通过以下命令解决：

brew update

brew install ruby

echo 'export PATH="/usr/local/opt/ruby/bin:$PATH"' >> ~/.bash_profile

source ~/.bash_profile

执行后，查看版本后，会判断已更新到最新版本。

\----------------------------------------------------------------------------------------------------------

关于ruby升级的问题：

已用home安装过ruby，升级： brew reinstall ruby



# How to install the latest ruby version on M1/M1 Pro/M1 Max Macs?

December 08, 2021 • 2 min read • [#iOS](https://antran.app/tags/iOS), [#Swift](https://antran.app/tags/Swift), [#MacBook](https://antran.app/tags/MacBook), [#M1](https://antran.app/tags/M1), [#tool](https://antran.app/tags/tool), [#ruby](https://antran.app/tags/ruby)

Ruby, for some reasons, has become an essential part of iOS Development tool belt. With popular tools written in Ruby such as [cocoapods](https://cocoapods.org/) or [fastlane](https://fastlane.tools/), installing Ruby is one of the first task most iOS developers do when setting up a new development environment.

Unfortunately, the preinstalled version of Ruby on Macs is outdated. For my new Macbook Pro 14 Inch (Dec 2021), the preinstalled Ruby is at version `2.6.8p205` . And the latest stable version of Ruby is `3.0.3`

In this article, I’ll show you some easy steps to install the latest Ruby version on your new MacBooks.

We are going to use [rbenv](https://github.com/rbenv/rbenv) to seamleassly manange the Ruby environment.

## Install rbenv

```text
# Install rbenv
brew install rbenv

# Initialise rbenv
rbenv init
```

## Verify rbenv

```shell
➜  ~ curl -fsSL https://github.com/rbenv/rbenv-installer/raw/main/bin/rbenv-doctor | bash

Checking for `rbenv' in PATH: /opt/homebrew/bin/rbenv
Checking for rbenv shims in PATH: OK
Checking `rbenv install' support: /opt/homebrew/bin/rbenv-install (ruby-build 20211203)
Counting installed Ruby versions: none
  There aren't any Ruby versions installed under `/Users/antran/.rbenv/versions'.
  You can install Ruby versions like so: rbenv install 3.0.3
Checking RubyGems settings: OK
Auditing installed plugins: OK
```

## Install ruby

List latest stable versions:

```shell
➜  ~ rbenv install -l
2.6.9
2.7.5
3.0.3
jruby-9.3.2.0
mruby-3.0.0
rbx-5.0
truffleruby-21.3.0
truffleruby+graalvm-21.3.0
```

Install Ruby 3.0.3

```shell
➜  ~ rbenv install 3.0.3
Downloading openssl-1.1.1l.tar.gz...
-> https://dqw8nmjcqpjn7.cloudfront.net/0b7a3e5e59c34827fe0c3a74b7ec8baef302b98fa80088d7f9153aa16fa76bd1
Installing openssl-1.1.1l...
Installed openssl-1.1.1l to /Users/antran/.rbenv/versions/3.0.3

Downloading ruby-3.0.3.tar.gz...
-> https://cache.ruby-lang.org/pub/ruby/3.0/ruby-3.0.3.tar.gz
Installing ruby-3.0.3...
ruby-build: using readline from homebrew
Installed ruby-3.0.3 to /Users/antran/.rbenv/versions/3.0.3
```

Set global version

```shell
 rbenv global 3.0.3
```

Verify

```shell
➜  ~ ruby -v
ruby 3.0.3p157 (2021-11-24 revision 3fb7d2cadc) [arm64-darwin21]
```