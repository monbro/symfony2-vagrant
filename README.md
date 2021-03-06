#Symfony 2 Vagrant Development setup


## Installation
####This setup is based and tested with Ubuntu Precise 64 bit base box, with Vagrant 1.0.5 version (should be vorking with 1.1)

* Install Vagrant using using the [installation instructions](http://docs.vagrantup.com/v2/installation/index.html)
* Clone this repository

    ```$ git clone https://github.com/irmantas/symfony2-vagrant.git```
    
* install git submodules
    ```$ git submodule update --init```

* run vagrant (for the first time it should take up to 10-15 min)
    ```$ vagrant up```
    
* Web server is accessible with http://33.33.33.100 (IP address can be changed in Vagrantfile)

* PhpMyAdmin is accessible with http://33.33.33.100/phpmyadmin

* Vagrant automatically setups database with this setup:

    * Username: symfony
    * Password: symfony-vagrant
    * Database: symfony

## Installed components

* [Nginx](http://nginx.org/en/) using puppet module from [example42](https://github.com/example42/puppet-nginx)
* [MySQL](http://www.mysql.com/) using puppet module from [example42](https://github.com/example42/puppet-mysql)
* [PHP-FPM](http://php-fpm.org/) (PHP 5.4)
* [PhpMyAdmin](http://www.phpmyadmin.net/home_page/index.php)
* [MongoDB](http://www.mongodb.org/)
* [Redis](http://redis.io/)
* [GiT](http://git-scm.com/)
* [Composer](http://getcomposer.org) installed globaly (use ```$ composer self-update``` to get the newest version)
* [Vim](http://www.vim.org/)
* [PEAR](http://pear.php.net/)
* [cURL](http://curl.haxx.se/)
* [Node.js](http://nodejs.org/)
* [npm](https://npmjs.org/)
* [less](http://lesscss.org/)
* [OpenJDK](http://openjdk.java.net/)
* [sass](http://sass-lang.com/)
* [Compass](http://compass-style.org/)
* [Imagic](http://www.imagemagick.org/script/index.php)
* [Capistrano](https://github.com/capistrano/capistrano)
* [Capifony](http://capifony.org/)
* [phpqatools](http://phpqatools.org/) using puppet module from ([https://github.com/rafaelfelix/puppet-phpqatools](https://github.com/rafaelfelix/puppet-phpqatools))
* [memcached](http://memcached.org/)

## Thanks to

* [example42](https://github.com/example42) - for great nginx\mysql templates
* [caramba1337](https://github.com/caramba1337) - for great ideas
* [kertz](https://github.com/kertz) - for great ideas
* [Markus Fischer](https://github.com/mfn) - for contribution

## Hints
####Startup speed
To speed up the startup process use ```$ vagrant up --no-provision``` (thanks to [caramba1337](https://github.com/caramba1337))

####Install Symfony Standard edition
* SSH to vagrant ```$ vagrant ssh```
* Clone symfony standard edition to somewhere temporary
    
    ```$ git clone https://github.com/symfony/symfony-standard.git /tmp/symfony```
    
* Move symfony repository to server document root

    ```$ mv /tmp/symfony/.git /vagrant/www/```

* Reset repository to restore project files
    
    ```$ cd /vagrant/www && git reset --hard HEAD```

* Install dependencies

    ```$ cd /vagrant/www && composer update```
    
* Edit ```web/app_dev.php``` to allow host

## Set up Shortcuts

* connect to you vagrant via 'vagrant ssh'

* open the profile file

    ```vi ~/.bashrc```

* go to the end by pressing 'shif + g'

* insert the commands by pressing 'i' and navigate by the arrow-keys and return to a new line

```
alias 0cc="php app/console cache:clear;"
alias 0cct="php app/console cache:clear --env=test;"
alias 0kp="php app/console cache:clear;php app/console doctrine:mongo:fixture;php app/console assetic:dump;php app/console fos:js-routing:dump;"
alias 0kk="php app/console cache:clear;php app/console doctrine:mongo:fixture;php app/console assetic:dump;php app/console fos:js-routing:dump;node_modules/karma/bin/karma start app/config/karma.conf.js;node_modules/karma/bin/karma start app/config/karma-e2e-client.conf.js;node_modules/karma/bin/karma start app/config/karma-e2e-globaladmin.conf.js;"
alias 0kcp="node_modules/karma/bin/karma start app/config/karma-e2e-client.conf.js;"
alias 0kc="node_modules/karma/bin/karma start app/config/karma-e2e-client.conf.js --browsers hookitup;"
alias 0kgp="node_modules/karma/bin/karma start app/config/karma-e2e-globaladmin.conf.js;"
alias 0kg="node_modules/karma/bin/karma start app/config/karma-e2e-globaladmin.conf.js --browsers hookitup;"
```

* exit the insert mode by pressing 'esc' button and save by pressing ':' and 'w' and hit return

* exit the file by pressing ':' and 'q' and hit return

* enter a 'bash -r' to refresh your bash window to be able to use the shortcuts

* use a shortcut simply by using 'cc' or 'kk'

## TODO
You tell me

## Special Notes

Go into you vagrant by

    vagrant ssh

We need to install the mongo php driver for php for some reason http://php.net/manual/en/mongo.installation.php simply by calling

    sudo pecl install mongo

Now exit your "vagrant ssh" via "exit" and reboot teh VM by the commends:

    vagrant halt
    vagrant up
    
For some reason, the new php5-fpm is not installed as well, according to http://askubuntu.com/questions/326681/php5-fpm-php-5-5-wont-install-cant-install-libsystemd-daemon0
 try :
 
    sudo add-apt-repository -y ppa:ondrej/systemd
    sudo apt-get update
    sudo apt-get install -y php5-fpm
    
In case php5-fpm is not running (check by using "service php5-fpm status") you can start it with

    sudo service php5-fpm start
    
And just in case, maybe we want to restart nginx
    
    sudo service nginx restart
    
And to make the vagrant accesible by intel.partnermarketing2.com and partenrmarketing2.com just append (MAC OSX) to your real machine at /etc/hosts
  
    33.33.33.100    domain.com
    33.33.33.100    subdomain.domain.com
    
To update your nodejs / node / npm

   http://stackoverflow.com/questions/16302436/install-nodejs-on-ubuntu-12-10
