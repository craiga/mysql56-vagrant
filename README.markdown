Vagrant-managed virtual maching running MySQL 5.6.

root user password is `root`.

Server is running on the default port (3306), which is mapped to 3336 on the host.

Connect to it as if it were running on your machine, only use port 3336.

    mysql --host=127.0.0.1 --port=3336 --user root --password

Heavily inspired my [mysql-vagrant](https://github.com/AlexDisler/mysql-vagrant).
