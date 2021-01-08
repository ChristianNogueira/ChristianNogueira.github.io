---
title: "After Ubuntu:20.04 LTS fresh install"
categories:
  - Blog
tags:
  - linux
---

Things to do after a Ubuntu fresh install, currently for LTS 20.04.

Update and upgrate

```bash
sudo apt-get update && sudo apt-get upgrade
```

Install Vim, Git and Curl. Upgrade to SpaceVim

```
sudo apt install vim git curl -y && curl -sLf https://spacevim.org/install.sh | bash
```

Working with WordPress

 - Install PHP, Ngnix and MariaDB

```
sudo add-apt-repository ppa:ondrej/php
sudo apt-get install php7.4 php7.4-mysql php7.4-curl php7.4-json php7.4-cgi php7.4-xsl php7.4-xml php7.4-fpm php7.4-zip php7.4-mbstring php7.4-gd mariadb-server php7.4-xdebug
```

 - Install Composer

```
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer
```

 - Install Laravel

```
composer global require laravel/installer
echo 'export PATH="~/.config/composer/vendor/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

 - Install WordPress

```
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```

Docker

```
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

IDEs

```
sudo snap install phpstorm --classic
sudo snap install datagrip --classic
sudo snap install pycharm-community --classic
```

Others

```
sudo snap install slack --classic
sudo snap install spotify
```
