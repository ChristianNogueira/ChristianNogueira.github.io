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
sudo apt-get update && sudo apt-get upgrade -y
```

Install Chromium
```bash
sudo apt install chromium-browser -y
```

Install Vim, Git, Curl and pip. Upgrade to SpaceVim

```bash
sudo apt install vim-gtk git curl python3-pip -y
curl -sLf https://spacevim.org/install.sh | bash
```

Working with WordPress

 - Install PHP, Ngnix and MariaDB

```bash
sudo apt install ngnix mariadb-server
sudo add-apt-repository ppa:ondrej/php
sudo apt install php7.4 php7.4-mysql php7.4-curl php7.4-json php7.4-cgi php7.4-xsl php7.4-xml php7.4-fpm php7.4-zip php7.4-mbstring php7.4-gd php7.4-xdebug
```

 - Install Composer

```bash
curl -sS https://getcomposer.org/installer | php
sudo mv composer.phar /usr/local/bin/composer
chmod +x /usr/local/bin/composer
```

 - Install WordPress

```bash
curl -O https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar
chmod +x wp-cli.phar
sudo mv wp-cli.phar /usr/local/bin/wp
```

Install Laravel

```bash
composer global require laravel/installer
echo 'export PATH="~/.config/composer/vendor/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

Docker

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sh get-docker.sh
```

Java

```bash
sudo apt install openjdk-8-jdk -y
```

Kafka

reference: https://kafka.apache.org/downloads

```bash
curl -O https://ftp.cixug.es/apache/kafka/2.7.0/kafka_2.13-2.7.0.tgz
mv kafka_2.13-2.7.0.tgz ~/kafka_2.13-2.7.0.tgz
tar -xvf kafka_2.13-2.7.0.tgz
rm kafka_2.13-2.7.0.tgz
echo 'export PATH="home/'$USER'/kafka_2.13-2.7.0:$PATH"' >> ~/.bashrc
```

IDEs

```bash
sudo snap install phpstorm --classic
sudo snap install datagrip --classic
sudo snap install pycharm-community --classic
sudo snap install intellij-idea-community --classic
```

Others

```bash
sudo snap install slack --classic
sudo snap install spotify
```

```bash
sudo apt install gnome-tweaks gnome-clocks -y
```

AWS Cli
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
rm awscliv2.zip
rm -r aws/
```

SSH keys

```bash
chmod 600 key
chmod 600 key.pub
```
