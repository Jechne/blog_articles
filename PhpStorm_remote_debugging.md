# Setting PhpStorm debugging on remote [dev] machine

Lets suppose following environment. There is develop (physical) machine with Vmware where guest Linux (Ubuntu 14.04) is running. This guest is used as developlment server and contains EMP stack (NGINX, MySQL, PHP[-FPM]).  I am using PHPStorm v.9. How to set it up ?

## Remote interpreter
Here are some tutorials how to set remote interpreter in PhpStorm [[1]](https://www.jetbrains.com/phpstorm/help/configuring-remote-php-interpreters.html), [[2]](https://confluence.jetbrains.com/display/PhpStorm/Working+with+Remote+PHP+Interpreters+in+PhpStorm), [[3]](http://blog.jetbrains.com/phpstorm/2014/04/php-remote-interpreters-support-in-phpstorm-8-eap/)
As for 08/15/2015 PhpStorm is able to use only CLI  php.ini, so you should put all related settings to cli/php.ini. 

## Remote debugger
Be sure you will run Xdebug on guest system on port different than 9000, because there is a fpm running on that port. Set 9001 or 10000. Then you will just setup Debuger in PhpStorm Preferences. When configuring xdebug extension on guest, you don't need to set autostart on, there are lots of handy plugins for Chrome [[4]](https://chrome.google.com/webstore/detail/xdebug-helper/eadndfjplgieldjbigjakmdgkmoaaaoc) or Firefox .. All you need is set xdebug.idekey as "PHPSTORM". 

## Server settings
Languages & Frameworks -> PHP -> Servers
Your server is remote so you should add new server with app, port ( this is http port so 80 ) and debugger (Xdebug). Don't forget to set mapping for local / remote files. My Vmware setup uses shared folders so i need to use /mnt/hgfs/ .. 
If you are deploying through SFTP, you can use mapping from there..

Profit?!?
