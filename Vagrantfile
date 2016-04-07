# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"
  config.vm.network "forwarded_port", guest: 3306, host: 3336
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end
  config.vm.provision "shell", inline: <<-SHELL
    apt-get update
    debconf-set-selections <<< 'mysql-server-5.6 mysql-server/root_password password root'
    debconf-set-selections <<< 'mysql-server-5.6 mysql-server/root_password_again password root'
    apt-get install -y mysql-server-5.6
    mysql -u root -proot <<< "GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'root';"
    sed -ri 's/^bind-address.*/bind-address = */g' /etc/mysql/my.cnf
    service mysql restart
  SHELL
end
