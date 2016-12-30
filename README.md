1. 安装gitlab（安装在/opt目录下）

在bitnami下载gitlab安装包：http://bitnami.com/stack/gitlab

$ wget http://downloads.bitnami.com/files/stacks/gitlab/5.3.0-1/bitnami-gitlab-6.3.0-0-linux-x64-installer.run
$ chmod 755 bitnami-gitlab-6.3.0-0-linux-x64-installer.run
$ sudo ./bitnami-gitlab-6.3.0-0-linux-x64-installer.run
OpenSSH server

$ sudo apt-get remove iptables
$ sudo apt-get install openssh-server
$ sudo chmod 755 ctlscript.sh
$ sudo ./ctlscript.sh start

2. 配置git（http://git-scm.com/book/en/Customizing-Git-Git-Configuration）

$ git config –global color.ui true
$ git config –global user.name “”your_name””
$ git config –global user.email “”your_email@example.com””

3. 配置ssh key

$ ssh-keygen -t rsa -C “”your_email@example.com””
$ ssh-add id_rsa

$ sudo apt-get install xclip
$ xclip -sel clip < ~/.ssh/id_rsa.pub

添加到git

$ ssh -T git@github.com

4. 搭建ruby环境
* 安装必要包：

$ sudo apt-get install build-essential bison openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-0 libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev libicu-dev

* 安装rbenv：

$ cd ~
curl https://raw.githubusercontent.com/fesplugas/rbenv-installer/master/bin/rbenv-installer | bash
rbenv install 2.1.0
rbenv global 2.1.0
$ vi ~/.bashrc
输入：
export RBENV_ROOT=””${HOME}/.rbenv””
if [ -d “”${RBENV_ROOT}”” ]; then
export PATH=””${RBENV_ROOT}/bin:${PATH}””
eval “”$(rbenv init -)””
fi

(curl -fsSL https://gist.github.com/mislav/a18b9d7f0dc5b9efc162.txt | rbenv install –patch 2.1.1)

$ source ~/.bashrc
$ rbenv bootstrap-ubuntu-12-04
* 安装ruby：

$ rbenv install 1.9.3-p392
$ rbenv rehash
$ rbenv global 1.9.3-p392
* 检查ruby是否安装成功：

$ ruby -v # => ruby 1.9.3p484 (2013-11-22 revision 43786) [x86_64-linux]

* 检查 OpenSSL是否安装：

$ irb
$ require ‘openssl’ # => true

$ echo “”gem: –no-ri –no-rdoc”” > ~/.gemrc

* 安装rails：

$ gem install bundler
$ gem install rake
$ rbenv rehash
$ gem install rails

* 配置默认Ruby版本

$ rbenv global 1.9.3-p484
* 项目bundle

$ cd <project path>
$ bundle install

5. 安装nodejs

$ sudo add-apt-repository ppa:chris-lea/node.js
$ sudo apt-get update
$ sudo apt-get install nodejs

6. 安装mysql：

$ sudo apt-get install mysql-server

7. gem 依赖包
rmagick

$ sudo apt-get install graphicsmagick-libmagick-dev-compat(or libmagickwand-dev)
mysql2

$ sudo apt-get install libmysql-ruby libmysqlclient-dev

pg

$ sudo apt-get install libpq-dev

8. 整合bitanami安装的gitlab
添加mysql路径

$ vi ~/.bashrc
$ export PATH=””<mysql_PATH>/mysql/bin:${PATH}””

启动gitlab服务：

$ sudo bash ctlscript.sh help
$ sudo bash ctlscript.sh restart mysql

9. gem curb

$ sudo apt-get install libcurl3-dev

10. zsh

$ sudo apt-get install zsh

11. 添加mysql path

$ vi .bashrc
/opt/gitlab-xxx/mysql/bin:

12. 创建repositories

$ cd /home/git && mkdir repositories
$ sudo chown -R xxx:xxx repositoties

13. imagemagick

14. libv8 (mac)

$ sudo -u git -H bash -l -c ‘bundle config build.libv8 –with-system-v8′

$ brew tap homebrew/dupes # Thanks Tom
$ brew install apple-gcc42

$ export CC=/usr/local/Cellar/apple-gcc42/4.2.1-5666.3/bin/gcc-4.2
$ export CXX=/usr/local/Cellar/apple-gcc42/4.2.1-5666.3/bin/g++-4.2
$ export CPP=/usr/local/Cellar/apple-gcc42/4.2.1-5666.3/bin/cpp-4.2

$ brew uninstall v8

$ gem uninstall libv8

$ gem install therubyracer -v ‘0.10.2’ # specify version

$ sudo apt-get install libdjvulibre-dev libjpeg-dev libtiff-dev libwmf-dev libmagickcore-dev libmagickwand-dev libmagick++-dev imagemagick
$ gem install rmagick
参考：

http://gorails.com/setup/ubuntu/13.10

https://help.github.com/articles/generating-ssh-keys

http://git-scm.com/book/en/Customizing-Git-Git-Configuration

https://gist.github.com/v1nc3ntlaw/1631411

https://www.digitalocean.com/community/articles/how-to-install-ruby-on-rails-on-ubuntu-12-04-lts-with-rbenv–2″
